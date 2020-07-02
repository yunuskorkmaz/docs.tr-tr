---
ms.openlocfilehash: 809ca85b347fabc44573e2e0c5a43261d68590d3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621395"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="dbed0-101">İş akışı SQL kalıcılığı birincil anahtar kümeleri ekler ve bazı sütunlarda null değerlere izin vermez</span><span class="sxs-lookup"><span data-stu-id="dbed0-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

#### <a name="details"></a><span data-ttu-id="dbed0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="dbed0-102">Details</span></span>

<span data-ttu-id="dbed0-103">.NET Framework 4,7 ' den başlayarak, SQL Workflow örnek deposu (SWU) için SqlWorkflowInstanceStoreSchema. SQL betiği tarafından oluşturulan tablolar kümelenmiş birincil anahtarları kullanır.</span><span class="sxs-lookup"><span data-stu-id="dbed0-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="dbed0-104">Bu nedenle, kimlikler <code>null</code> değerleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="dbed0-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="dbed0-105">SWSıS işlemi bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="dbed0-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="dbed0-106">SQL Server Işlemsel çoğaltmayı desteklemek için güncelleştirmeler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="dbed0-106">The updates were made to support SQL Server Transactional Replication.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dbed0-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="dbed0-107">Suggestion</span></span>

<span data-ttu-id="dbed0-108">Bu değişikliğe yönelik olarak, SqlWorkflowInstanceStoreSchemaUpgrade. sql dosyasının mevcut yüklemelere uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbed0-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="dbed0-109">Yeni veritabanı yüklemeleri otomatik olarak değişikliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="dbed0-109">New database installations will automatically have the change.</span></span>

| <span data-ttu-id="dbed0-110">Name</span><span class="sxs-lookup"><span data-stu-id="dbed0-110">Name</span></span>    | <span data-ttu-id="dbed0-111">Değer</span><span class="sxs-lookup"><span data-stu-id="dbed0-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dbed0-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="dbed0-112">Scope</span></span>   |<span data-ttu-id="dbed0-113">Edge</span><span class="sxs-lookup"><span data-stu-id="dbed0-113">Edge</span></span>|
|<span data-ttu-id="dbed0-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dbed0-114">Version</span></span>|<span data-ttu-id="dbed0-115">4,7</span><span class="sxs-lookup"><span data-stu-id="dbed0-115">4.7</span></span>|
|<span data-ttu-id="dbed0-116">Tür</span><span class="sxs-lookup"><span data-stu-id="dbed0-116">Type</span></span>|<span data-ttu-id="dbed0-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="dbed0-117">Runtime</span></span>|
