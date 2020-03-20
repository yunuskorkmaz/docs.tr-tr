---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802454"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="00c0a-101">İş akışı SQL kalıcılığı birincil anahtar kümeleri ekler ve bazı sütunlarda null değerleri izin vermez</span><span class="sxs-lookup"><span data-stu-id="00c0a-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="00c0a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="00c0a-102">Details</span></span>|<span data-ttu-id="00c0a-103">.NET Framework 4.7 ile başlayarak, SQLWorkflowInstanceStoreSchema.sql komut dosyası tarafından SQL İş Akışı Örnek Deposu (SWIS) için oluşturulan tablolar kümelenmiş birincil tuşları kullanır.</span><span class="sxs-lookup"><span data-stu-id="00c0a-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="00c0a-104">Bu nedenle, kimlikler değerleri <code>null</code> desteklemez.</span><span class="sxs-lookup"><span data-stu-id="00c0a-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="00c0a-105">SWIS'in çalışması bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="00c0a-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="00c0a-106">Güncelleştirmeler SQL Server Transactional Replication desteklemek için yapıldı.</span><span class="sxs-lookup"><span data-stu-id="00c0a-106">The updates were made to support SQL Server Transactional Replication.</span></span>|
|<span data-ttu-id="00c0a-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="00c0a-107">Suggestion</span></span>|<span data-ttu-id="00c0a-108">Sql dosyası SqlWorkflowInstanceStoreSchemaUpgrade.sql bu değişikliği deneyimlemek için varolan yüklemelere uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00c0a-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="00c0a-109">Yeni veritabanı yüklemeleri otomatik olarak değişiklik olacaktır.</span><span class="sxs-lookup"><span data-stu-id="00c0a-109">New database installations will automatically have the change.</span></span>|
|<span data-ttu-id="00c0a-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="00c0a-110">Scope</span></span>|<span data-ttu-id="00c0a-111">Edge</span><span class="sxs-lookup"><span data-stu-id="00c0a-111">Edge</span></span>|
|<span data-ttu-id="00c0a-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="00c0a-112">Version</span></span>|<span data-ttu-id="00c0a-113">4.7</span><span class="sxs-lookup"><span data-stu-id="00c0a-113">4.7</span></span>|
|<span data-ttu-id="00c0a-114">Tür</span><span class="sxs-lookup"><span data-stu-id="00c0a-114">Type</span></span>|<span data-ttu-id="00c0a-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="00c0a-115">Runtime</span></span>|
