# moodle

drop database if exists MoodleDB;
create database MoodleDB;
use MoodleDB;

create table assign (
    id bigint(10) not null primary key auto_increment,
    course bigint(10) not NULL,
    name VARCHAR(255) not NULL,
    intro longtext not null,
    introformat SMALLINT(4) not null,
    alwaysshowdescription TINYINT(2) not null,
    nosubmissions TINYINT(2) not null,
    submissiondrafts TINYINT(2) not null,
    sendnotifications TINYINT(2) not null,
    sendlatenotifications TINYINT(2) not null,
    duedate bigint(10) not null,
    allowsubmissionfromdate bigint(10) not null,
    grade bigint(10) not NULL,
    timemodified bigint(10) not null,
    requiresubmissionstatement TINYINT(2) not null,
    completionsubmit TINYINT(2) not null,
    cutoffdate bigint(10) not null,
    teamsubmission TINYINT(2) not null,
    requireallteammemberssubmit TINYINT(2) not null,
    teamsubmissiongroupingid bigint(10) not null,
    blindmarking TINYINT(2) not null,
    revealidentities TINYINT(2) not null,
    attemptreopenmethod VARCHAR(10) not null,
    maxattempts mediumint(6) not null,
    markingworkflow TINYINT(2) not null,
    markingallocation TINYINT(2) not null,
    sendstudentnotifications TINYINT(2) not NULL
);

create table assignfeedback_comments (
     id bigint(10) not null primary key auto_increment,
     assignment bigint(10) not null,
     grade bigint(10) not null,
     commenttext longtext not null,
     commentformat SMALLINT(4)
);

create table assignfeedback_editpdf_annot (
     id bigint(10) not null primary key auto_increment,
     gradeid bigint(10) not null,
     pageno bigint(10) not null,
     x bigint(10) not null,
     y bigint(10) not null,
     endx bigint(10) not null,
     endy bigint(10) not null,
     path longtext not null,
     type VARCHAR(10) not null,
     colour VARCHAR(10) not null,
     draft TINYINT(2) not NULL
);

create table assign_user_mapping (
     id bigint(10) not null primary key auto_increment,
     assignment bigint(10) not null,
     userid bigint(10) not null
     );

create table assign_grades (
     id bigint(10) not null primary key auto_increment,
     assignment bigint(10) not null,
     userid bigint(10) not null,
     timecreated bigint(10) not NULL,
     timemodified bigint(10) not null,
     grader bigint(10) not NULL,
     grade DECIMAL(10,5) not null,
     attemptnumber bigint(10) not null
    );

create table assignfeedback_editpdf_cmnt (
     id bigint(10) not null primary key auto_increment,
     gradeid bigint(10) not NULL,
     x bigint(10) not null,
     y bigint(10) not null,
     width bigint(10) not null,
     rawtext longtext not NULL,
     pageno bigint(10) not NULL,
     colour VARCHAR(10) not null,
     draft TINYINT(2)
);

create table assignfeedback_editpdf_quick (
     id bigint(10) not null primary key auto_increment,
     userid bigint(10) not NULL,
     rawtext longtext not NULL,
     width bigint(10) not NULL,
     colour VARCHAR(10) not NULL
);

create table assignfeedback_file (
     id bigint(10) not null primary key auto_increment,
     assignment bigint(10) not NULL,
     grade bigint(10) not NULL,
     numfiles bigint(10) not NULL
);

create table assign_user_flags (
     id bigint(10) not null primary key auto_increment,
     userid bigint(10) not null,
     assignment bigint(10) not null,
     locked bigint(10) not NULL,
     mailed SMALLINT(4) not NULL,
     extensionduedate bigint(10) not null,
     workflowstate VARCHAR(20) not NULL,
     allocatedmarker bigint(10) not NULL
);

create table assignsubmission_onlinetext (
     id bigint(10) not null primary key auto_increment,
     assignment bigint(10) not NULL,
     submission bigint(10) not NULL,
     onlinetext longtext not NULL,
     onlineformat SMALLINT(4) not NULL
);

create table assignsubmission (
     id bigint(10) not null primary key auto_increment,
     assignment bigint(10) not NULL,
     userid bigint(10) not null,
     timecreated bigint(10) not NULL,
     timemodified bigint(10) not NULL,
     status VARCHAR(10) not NULL,
     groupid bigint(10) not NULL,
     attemptnumber bigint(10) not NULL
);

create table assignsubmission_file (
     id bigint(10) not null primary key auto_increment,
     assignment bigint(10) not NULL,
     submission bigint(10) not NULL,
     numfiles bigint(10) not NULL
);

create table assign_plugin_config (
     id bigint(10) not null primary key auto_increment,
     assignment bigint(10) not NULL,
     plugin VARCHAR(28) not NULL,
     subtype VARCHAR(28) not NULL,
     name VARCHAR(28) not NULL,
     value longtext not NULL
);
