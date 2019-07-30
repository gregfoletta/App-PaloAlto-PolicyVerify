# NAME

App::PaloAlto::LogTest - Test firewall rules using log files.

# VERSION

version 0.1.1

# SYNOPSIS

# DESCRIPTION

# METHODS

## new

    my $fw_tester = Device::Firewall::PaloAlto::LogTest->new(
        uri => 'https://pa.local',
        username => 'admin',
        password => 'redacted',
        verify_hostname => 0
    ); 

## sep

Sets the separating character between the fields

## logfile 

    $fw_tester->logfile('/home/user/logfile.csv');

Opens a logfile with traffic entries to be run against the firewall

## run

Runs the current configuration against the firewall.

# AUTHOR

Greg Foletta <greg@foletta.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2019 by Greg Foletta.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
