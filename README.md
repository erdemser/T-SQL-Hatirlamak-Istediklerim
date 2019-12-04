SQL Server’da Mükerrer Kayıtları Bulma

Select KolonAdi, Count(KolonAdi) From TabloAdi Group By KolonAdi Having Count (KolonAdi) > 1
