# NAME

App::PaloAlto::PolicyVerify - Test firewall rules using log files.

# VERSION

version 0.0.1

# SYNOPSIS

This is the supporting module for the [pa\_policy\_verify](https://metacpan.org/pod/pa_policy_verify) application.

# DESCRIPTION

This module contains the methods used by the [pa\_policy\_verify](https://metacpan.org/pod/pa_policy_verify) application.
It takes in information allowing it to connect to a Palo Alto firewall, and a logfile containing
flows - source/destination IP & ports, and a protocol.

It then runs each flow in the log against the security rulebase currently installed on the Palo Alto firewall 
and returns a result. The result contains:

- Which rule the flow would have hit
- The action the rule takes
- The index of the rule.

The main use case is when migrating from a different firewall to the Palo Alto. It allows for the 
qualification of the migrated rulebase prior to the cutover of production flows.

# METHODS

## new

    my $fw_tester = App::PaloAlto::PolicyVerify->new(
        uri => 'https://pa.localdomain',
        username => 'admin',
        password => 'redacted',
        insecure => 0,
        vr => 'default',
        vsys => 1,
        logfile => '/home/user/logs.csv',
        sepchar => ',',
        fields => '0,1,2,3,4'
    );

Contructs the object. Each argument maps to a command line switch in [pa\_policy\_verify](https://metacpan.org/pod/pa_policy_verify). Please refer to its
documentation for information and default values.

The only argument without a default is `logfile`.

## sepchar

    $fw_tester->sepchar(';');

Sets the separating character between the fields in the logfile.

## logfile 

    $fw_tester->logfile('/home/user/logfile.csv');

Sets the logfile containing flow information that will be run against the firewall.

## fields

    $fw_tester->fields(
        src_ip => 3,
        dst_ip => 4,
        src_port => 8,
        dst_port => 9,
        protocol => 20
    );

Sets the column number in the logfile where each of the 5-tuple flow information resides.

## run

    $fw_tester->run();

Runs the flows contained in the logfile against the firewall.

# AUTHOR

Greg Foletta <greg@foletta.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2019 by Greg Foletta.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
