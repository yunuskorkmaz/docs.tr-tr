---
title: Çevrimiçi yedekleme
ms.date: 12/13/2019
description: SQLite 'un çevrimiçi yedekleme özelliğini nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: d857dcb69f2b2d10b034a0abf222b30c2e20bb41
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901278"
---
# <a name="online-backup"></a>Çevrimiçi yedekleme

Bir uygulama çalışırken SQLite, veritabanı dosyalarını yedekleyebilir. Bu işlevsellik, `SqliteConnection`<xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> yöntemi olarak Microsoft. Data. SQLite 'ta kullanılabilir.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

Şu anda `BackupDatabase`, veritabanını olabildiğince çabuk yedekleyecek ve diğer bağlantıların veritabanına yazmasını engeller. Sorun [#13834](https://github.com/dotnet/efcore/issues/13834) , arka planda veritabanını yedeklemek ve diğer bağlantıların yedeklemeyi kesintiye uğratmak ve veritabanına yazmak için ALTERNATIF bir API sağlar. İlgilendiğiniz sorun hakkında geri bildirim sağlayın.
