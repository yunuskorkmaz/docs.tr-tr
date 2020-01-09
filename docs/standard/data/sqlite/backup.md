---
title: Çevrimiçi yedekleme
ms.date: 12/13/2019
description: SQLite 'un çevrimiçi yedekleme özelliğini nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 885aa2c5555b58deb2551c0a4e6933742a093457
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447099"
---
# <a name="online-backup"></a>Çevrimiçi yedekleme

Bir uygulama çalışırken SQLite, veritabanı dosyalarını yedekleyebilir. Bu işlevsellik, `SqliteConnection`<xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> yöntemi olarak Microsoft. Data. SQLite 'ta kullanılabilir.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

Şu anda `BackupDatabase`, veritabanını olabildiğince çabuk yedekleyecek ve diğer bağlantıların veritabanına yazmasını engeller. Sorun [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) , arka planda veritabanını yedeklemek ve diğer bağlantıların yedeklemeyi kesintiye uğratmak ve veritabanına yazmak için ALTERNATIF bir API sağlar. İlgilendiğiniz sorun hakkında geri bildirim sağlayın.
