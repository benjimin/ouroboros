# ouroboros
Recurring task scheduler for compute clusters that provide *PBS* but not *cron*.

The constraints of this problem make the solutions inherently fragile and non-ideal.

## Design
Ouroboros core is intended to persistently reschedule itself and the cron-daemon equivalent (crondlike), via PBS, and to issue alerts if crondlike breaks. Ouroboros is intended to be as robust as possible.

Crondlike is to facilitate customisable regular (e.g. daily or weekly) tasks, e.g. *polling* for work. Small tasks may occur in the same process, but separate PBS jobs will be scheduled for larger tasks.

An optional locking mechanism will ensure a task is not instantiated twice (if it continues for a longer period than the polling frequency). 

Some mechanism will be used to dispatch notifications reliably.

Some mechanism will be used to test for unsuccessful jobs.

## Example applications

- synchronising local and remote databases
- polling for unprocessed data and updating downstream products

