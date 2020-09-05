---
ms.openlocfilehash: fd9f4f3de8f7be39242d4ff6924d480f20a1a06b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497508"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a><span data-ttu-id="c5803-101">SqlBulkCopy dizeler için hedef sütun kodlamasını kullanır</span><span class="sxs-lookup"><span data-stu-id="c5803-101">SqlBulkCopy uses destination column encoding for strings</span></span>

#### <a name="details"></a><span data-ttu-id="c5803-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c5803-102">Details</span></span>

<span data-ttu-id="c5803-103">Bir sütuna veri eklenirken, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> ve türleri için varsayılan kodlama yerine, hedef sütunun kodlamasını kullanır <code>VARCHAR</code> <code>CHAR</code> .</span><span class="sxs-lookup"><span data-stu-id="c5803-103">When inserting data into a column, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> uses the encoding of the destination column rather than the default encoding for <code>VARCHAR</code> and <code>CHAR</code> types.</span></span> <span data-ttu-id="c5803-104">Bu değişiklik, hedef sütun varsayılan kodlamayı kullanmadığında varsayılan kodlamayı kullanarak neden olunan veri bozulması olasılığını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c5803-104">This change eliminates the possibility of data corruption caused by using the default encoding when the destination column does not use the default encoding.</span></span> <span data-ttu-id="c5803-105">Nadir durumlarda, Kodlamadaki değişiklik hedef sütuna sığmayacak kadar büyük veriler üretirse, mevcut bir uygulama bir SqlException özel durumu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="c5803-105">In rare cases, an existing application may throw a SqlException exception if the change in encoding produces data that is too big to fit into the destination column.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c5803-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="c5803-106">Suggestion</span></span>

<span data-ttu-id="c5803-107"><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName>Kodlama farklılıkları nedeniyle artık verileri bozmayacak.</span><span class="sxs-lookup"><span data-stu-id="c5803-107">Expect that <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> will no longer corrupt data due to encoding differences.</span></span> <span data-ttu-id="c5803-108">Hedef sütunun boyut sınırına yakın olan dizeler kopyalanırsa, verilerin önceden kodlanması gerekebilir (verilerin hedef sütuna sığması için kopyalanması için) veya Catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="c5803-108">If strings near the destination column's size limit are being copied, it may be necessary to either pre-encode data (to be copied to check that the data will fit in the destination column) or catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="c5803-109">Name</span><span class="sxs-lookup"><span data-stu-id="c5803-109">Name</span></span>    | <span data-ttu-id="c5803-110">Değer</span><span class="sxs-lookup"><span data-stu-id="c5803-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c5803-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c5803-111">Scope</span></span>   |<span data-ttu-id="c5803-112">Edge</span><span class="sxs-lookup"><span data-stu-id="c5803-112">Edge</span></span>|
|<span data-ttu-id="c5803-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c5803-113">Version</span></span>|<span data-ttu-id="c5803-114">4,5</span><span class="sxs-lookup"><span data-stu-id="c5803-114">4.5</span></span>|
|<span data-ttu-id="c5803-115">Tür</span><span class="sxs-lookup"><span data-stu-id="c5803-115">Type</span></span>|<span data-ttu-id="c5803-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="c5803-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c5803-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c5803-117">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)>

<!--

#### Affected APIs

- `T:System.Data.SqlClient.SqlBulkCopy`
- `M:System.Data.SqlClient.SqlBulkCopy.#ctor(System.Data.SqlClient.SqlConnection)`

-->
