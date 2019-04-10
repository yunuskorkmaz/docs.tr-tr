---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236235"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="31201-101">İş akışı SQL kalıcılığını birincil anahtar kümeleri ve bazı sütunları null değerleri izin vermiyor ekler.</span><span class="sxs-lookup"><span data-stu-id="31201-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="31201-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="31201-102">Details</span></span>|<span data-ttu-id="31201-103">.NET Framework 4.7 ile başlayarak, SQL iş akışı örneği Store (SWIS) için SqlWorkflowInstanceStoreSchema.sql betiği tarafından oluşturulan tablolarda kümelenmiş birincil anahtarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="31201-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="31201-104">Bu nedenle, kimlikleri desteklemez <code>null</code> değerleri.</span><span class="sxs-lookup"><span data-stu-id="31201-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="31201-105">SWIS işlemi, bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="31201-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="31201-106">SQL Server işlem çoğaltmayı desteklemek için güncelleştirmeleri yapıldı.</span><span class="sxs-lookup"><span data-stu-id="31201-106">The updates were made to support SQL Server Transactional Replication.</span></span>|
|<span data-ttu-id="31201-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="31201-107">Suggestion</span></span>|<span data-ttu-id="31201-108">Bu değişiklik deneyimi için SQL dosyası SqlWorkflowInstanceStoreSchemaUpgrade.sql var olan yüklemeler için uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="31201-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="31201-109">Yeni veritabanı yüklemelerini değişikliği otomatik olarak sahip olur.</span><span class="sxs-lookup"><span data-stu-id="31201-109">New database installations will automatically have the change.</span></span>|
|<span data-ttu-id="31201-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="31201-110">Scope</span></span>|<span data-ttu-id="31201-111">Kenar</span><span class="sxs-lookup"><span data-stu-id="31201-111">Edge</span></span>|
|<span data-ttu-id="31201-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="31201-112">Version</span></span>|<span data-ttu-id="31201-113">4.7</span><span class="sxs-lookup"><span data-stu-id="31201-113">4.7</span></span>|
|<span data-ttu-id="31201-114">Tür</span><span class="sxs-lookup"><span data-stu-id="31201-114">Type</span></span>|<span data-ttu-id="31201-115">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="31201-115">Runtime</span></span>|
