---
ms.openlocfilehash: cb9305f623044233082286863d2f2d2c7e9d665a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497900"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="5738c-101">İş akışı SQL kalıcılığı birincil anahtar kümeleri ekler ve bazı sütunlarda null değerlere izin vermez</span><span class="sxs-lookup"><span data-stu-id="5738c-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

#### <a name="details"></a><span data-ttu-id="5738c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5738c-102">Details</span></span>

<span data-ttu-id="5738c-103">.NET Framework 4,7 ' den başlayarak, SQL Workflow örnek deposu (SWU) için SqlWorkflowInstanceStoreSchema. SQL betiği tarafından oluşturulan tablolar kümelenmiş birincil anahtarları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5738c-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="5738c-104">Bu nedenle, kimlikler <code>null</code> değerleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5738c-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="5738c-105">SWSıS işlemi bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="5738c-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="5738c-106">SQL Server Işlemsel çoğaltmayı desteklemek için güncelleştirmeler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5738c-106">The updates were made to support SQL Server Transactional Replication.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5738c-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="5738c-107">Suggestion</span></span>

<span data-ttu-id="5738c-108">Bu değişikliğe yönelik olarak, SqlWorkflowInstanceStoreSchemaUpgrade. sql dosyasının mevcut yüklemelere uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5738c-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="5738c-109">Yeni veritabanı yüklemeleri otomatik olarak değişikliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="5738c-109">New database installations will automatically have the change.</span></span>

| <span data-ttu-id="5738c-110">Name</span><span class="sxs-lookup"><span data-stu-id="5738c-110">Name</span></span>    | <span data-ttu-id="5738c-111">Değer</span><span class="sxs-lookup"><span data-stu-id="5738c-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5738c-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5738c-112">Scope</span></span>   |<span data-ttu-id="5738c-113">Edge</span><span class="sxs-lookup"><span data-stu-id="5738c-113">Edge</span></span>|
|<span data-ttu-id="5738c-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5738c-114">Version</span></span>|<span data-ttu-id="5738c-115">4,7</span><span class="sxs-lookup"><span data-stu-id="5738c-115">4.7</span></span>|
|<span data-ttu-id="5738c-116">Tür</span><span class="sxs-lookup"><span data-stu-id="5738c-116">Type</span></span>|<span data-ttu-id="5738c-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5738c-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5738c-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5738c-118">Affected APIs</span></span>

<span data-ttu-id="5738c-119">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="5738c-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
