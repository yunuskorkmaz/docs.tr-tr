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
# <a name="online-backup"></a><span data-ttu-id="30e73-103">Çevrimiçi yedekleme</span><span class="sxs-lookup"><span data-stu-id="30e73-103">Online backup</span></span>

<span data-ttu-id="30e73-104">Bir uygulama çalışırken SQLite, veritabanı dosyalarını yedekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="30e73-104">SQLite can back up database files while the app is running.</span></span> <span data-ttu-id="30e73-105">Bu işlevsellik, <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> Microsoft. Data. sqlite ' de yöntemi olarak sunulmaktadır `SqliteConnection`.</span><span class="sxs-lookup"><span data-stu-id="30e73-105">This functionality is available in Microsoft.Data.Sqlite as the <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> method on `SqliteConnection`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

<span data-ttu-id="30e73-106">`BackupDatabase` Şu anda veritabanını olabildiğince çabuk yedekleyecek ve diğer bağlantıların veritabanına yazmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="30e73-106">Currently, `BackupDatabase` will back up the database as quickly as possible and blocks other connections from writing to the database.</span></span> <span data-ttu-id="30e73-107">Sorun [#13834](https://github.com/dotnet/efcore/issues/13834) , arka planda veritabanını yedeklemek ve diğer bağlantıların yedeklemeyi kesintiye uğratmak ve veritabanına yazmak için ALTERNATIF bir API sağlar.</span><span class="sxs-lookup"><span data-stu-id="30e73-107">Issue [#13834](https://github.com/dotnet/efcore/issues/13834) would provide an alternative API to back up the database in the background and allow other connections to interrupt the backup and write to the database.</span></span> <span data-ttu-id="30e73-108">İlgilendiğiniz sorun hakkında geri bildirim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="30e73-108">If you're interested, provide feedback on the issue.</span></span>
