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
# <a name="online-backup"></a><span data-ttu-id="529d6-103">Çevrimiçi yedekleme</span><span class="sxs-lookup"><span data-stu-id="529d6-103">Online backup</span></span>

<span data-ttu-id="529d6-104">Bir uygulama çalışırken SQLite, veritabanı dosyalarını yedekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="529d6-104">SQLite can back up database files while the app is running.</span></span> <span data-ttu-id="529d6-105">Bu işlevsellik, `SqliteConnection`<xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> yöntemi olarak Microsoft. Data. SQLite 'ta kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="529d6-105">This functionality is available in Microsoft.Data.Sqlite as the <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> method on `SqliteConnection`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

<span data-ttu-id="529d6-106">Şu anda `BackupDatabase`, veritabanını olabildiğince çabuk yedekleyecek ve diğer bağlantıların veritabanına yazmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="529d6-106">Currently, `BackupDatabase` will back up the database as quickly as possible and blocks other connections from writing to the database.</span></span> <span data-ttu-id="529d6-107">Sorun [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) , arka planda veritabanını yedeklemek ve diğer bağlantıların yedeklemeyi kesintiye uğratmak ve veritabanına yazmak için ALTERNATIF bir API sağlar.</span><span class="sxs-lookup"><span data-stu-id="529d6-107">Issue [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) would provide an alternative API to back up the database in the background and allow other connections to interrupt the backup and write to the database.</span></span> <span data-ttu-id="529d6-108">İlgilendiğiniz sorun hakkında geri bildirim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="529d6-108">If you're interested, provide feedback on the issue.</span></span>
