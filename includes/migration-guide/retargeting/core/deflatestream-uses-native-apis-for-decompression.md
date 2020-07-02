---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614726"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a><span data-ttu-id="77400-101">DeflateStream, açma için yerel API 'Ler kullanır</span><span class="sxs-lookup"><span data-stu-id="77400-101">DeflateStream uses native APIs for decompression</span></span>

#### <a name="details"></a><span data-ttu-id="77400-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="77400-102">Details</span></span>

<span data-ttu-id="77400-103">.NET Framework 4.7.2 başlayarak, sınıfında açma işlemi, `T:System.IO.Compression.DeflateStream` Varsayılan olarak yerel Windows API 'lerini kullanacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="77400-103">Starting with the .NET Framework 4.7.2, the implementation of decompression in the `T:System.IO.Compression.DeflateStream` class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="77400-104">Genellikle bu, önemli ölçüde performans geliştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="77400-104">Typically, this results in a substantial performance improvement.</span></span> <span data-ttu-id="77400-105">.NET Framework sürüm 4.7.2 veya üstünü hedefleyen tüm .NET uygulamaları yerel uygulamayı kullanır. Bu değişiklik davranıştaki bazı farklılıklar oluşmasına neden olur ve şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="77400-105">All .NET applications targeting the .NET Framework version 4.7.2 or higher use the native implementation.This change might result in some differences in behavior, which include:</span></span>

- <span data-ttu-id="77400-106">Özel durum iletileri farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="77400-106">Exception messages may be different.</span></span> <span data-ttu-id="77400-107">Ancak, atılan özel durum türü aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="77400-107">However, the type of exception thrown remains the same.</span></span>
- <span data-ttu-id="77400-108">Bir işlemi tamamlamaya yetecek kadar bellek olmaması gibi bazı özel durumlar farklı şekilde işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="77400-108">Some special situations, such as not having enough memory to complete an operation, may be handled differently.</span></span>
- <span data-ttu-id="77400-109">Gzip üst bilgisini ayrıştırmak için bilinen farklar vardır (Note: yalnızca `GZipStream` açma için ayarlanan) etkilenir:</span><span class="sxs-lookup"><span data-stu-id="77400-109">There are known differences for parsing gzip header (note: only `GZipStream` set for decompression is affected):</span></span>
- <span data-ttu-id="77400-110">Geçersiz üstbilgileri ayrıştırırken özel durumlar farklı zamanlarda oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="77400-110">Exceptions when parsing invalid headers may be thrown at different times.</span></span>
- <span data-ttu-id="77400-111">Yerel uygulama, gzip üst bilgisindeki (yani [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) bazı ayrılmış bayraklar için bu değerleri, daha önce geçersiz değerlerin yoksayıldığı bir özel durum oluşturulmasına neden olabilen, belirtime göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="77400-111">The native implementation enforces that values for some reserved flags inside the gzip header (i.e. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) are set according to the specification, which may cause it to throw an exception where previously invalid values were ignored.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="77400-112">Öneri</span><span class="sxs-lookup"><span data-stu-id="77400-112">Suggestion</span></span>

<span data-ttu-id="77400-113">Yerel API 'Ler ile açma, uygulamanızın davranışını olumsuz yönde etkileiyorsa, `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` `runtime` app.config dosyanızın bölümüne anahtarı ekleyerek ve ayarlarını yaparak bu özelliği devre dışı bırakabilirsiniz `true` :</span><span class="sxs-lookup"><span data-stu-id="77400-113">If decompression with native APIs has adversely affected the behavior of your app, you can opt out of this feature by adding the `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` switch to the `runtime` section of your app.config file and setting it to `true`:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="77400-114">Name</span><span class="sxs-lookup"><span data-stu-id="77400-114">Name</span></span>    | <span data-ttu-id="77400-115">Değer</span><span class="sxs-lookup"><span data-stu-id="77400-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="77400-116">Kapsam</span><span class="sxs-lookup"><span data-stu-id="77400-116">Scope</span></span>   | <span data-ttu-id="77400-117">İkincil</span><span class="sxs-lookup"><span data-stu-id="77400-117">Minor</span></span>       |
| <span data-ttu-id="77400-118">Sürüm</span><span class="sxs-lookup"><span data-stu-id="77400-118">Version</span></span> | <span data-ttu-id="77400-119">4.7.2</span><span class="sxs-lookup"><span data-stu-id="77400-119">4.7.2</span></span>       |
| <span data-ttu-id="77400-120">Tür</span><span class="sxs-lookup"><span data-stu-id="77400-120">Type</span></span>    | <span data-ttu-id="77400-121">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="77400-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="77400-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="77400-122">Affected APIs</span></span>

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
