---
ms.openlocfilehash: 148312743dd274728b178951548889dc3a680528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614691"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a><span data-ttu-id="3f8a0-101">ZipArchiveEntry nesnelerinin FullName özelliğindeki yol ayırıcı karakterinde değişiklik</span><span class="sxs-lookup"><span data-stu-id="3f8a0-101">Change in path separator character in FullName property of ZipArchiveEntry objects</span></span>

#### <a name="details"></a><span data-ttu-id="3f8a0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3f8a0-102">Details</span></span>

<span data-ttu-id="3f8a0-103">.NET Framework 4.6.1 ve sonraki sürümlerini hedefleyen uygulamalar için yol ayırıcı karakteri, \" <xref:System.IO.Compression.ZipArchiveEntry.FullName> <xref:System.IO.Compression.ZipArchiveEntry> yöntemin aşırı yüklemeleri tarafından oluşturulan nesnelerin özelliğindeki ters eğik çizgiden (") eğik çizgiyle ("/") değiştirilmiştir <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f8a0-103">For apps that target the .NET Framework 4.6.1 and later versions, the path separator character has changed from a backslash ("\") to a forward slash ("/") in the <xref:System.IO.Compression.ZipArchiveEntry.FullName> property of <xref:System.IO.Compression.ZipArchiveEntry>  objects created by overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> method.</span></span> <span data-ttu-id="3f8a0-104">Bu değişiklik, .NET uygulamasını konusunun Bölüm 4.4.17.1 ile uyum sağlar [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve izin verir. ZIP arşivleri Windows dışı sistemlerde açılacak.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-104">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span><br /><span data-ttu-id="3f8a0-105">Macintosh gibi Windows dışı işletim sistemlerinde .NET Framework önceki bir sürümünü hedefleyen bir uygulama tarafından oluşturulan bir ZIP dosyasını açma işlemi, dizin yapısını koruyamaz.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-105">Decompressing a zip file created by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="3f8a0-106">Örneğin, Macintosh üzerinde, dosya adı dizin yolunu, herhangi bir ters eğik çizgi ("") karakteri ve dosya adıyla birleştiren bir dosya kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-106">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("") characters, and the filename.</span></span> <span data-ttu-id="3f8a0-107">Sonuç olarak, açılan dosyaların dizin yapısı korunmaz.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-107">As a result, the directory structure of decompressed files is not preserved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3f8a0-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="3f8a0-108">Suggestion</span></span>

<span data-ttu-id="3f8a0-109">Bu değişikliğin üzerinde etkisi. Windows işletim sisteminde .NET Framework ad alanındaki API 'Ler tarafından açılan ZIP dosyaları <xref:System.IO?displayProperty=nameWithType> en az olmalıdır. Bu API 'ler \" yol ayırıcı karakteri olarak eğik çizgi ("/") veya ters eğik çizgi (") sorunsuzca işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-109">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO?displayProperty=nameWithType> namespace should be minimal, since these APIs can seamlessly handle either a forward slash ("/") or a backslash ("\") as the path separator character.</span></span><br /><span data-ttu-id="3f8a0-110">Bu değişiklik istenmeyen ise, [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyanızın bölümüne bir yapılandırma ayarı ekleyerek bunu devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-110">If this change is undesirable, you can opt out of it by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="3f8a0-111">Aşağıdaki örnek hem `<runtime>` bölümünü hem de geri `Switch.System.IO.Compression.ZipFile.UseBackslash` çevirme anahtarını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3f8a0-111">The following example shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-out switch:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

<span data-ttu-id="3f8a0-112">Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 ve sonraki sürümlerde çalışan uygulamalar, [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının bölümüne bir yapılandırma ayarı ekleyerek bu davranışı kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-112">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="3f8a0-113">Aşağıda hem `<runtime>` bölümü hem de `Switch.System.IO.Compression.ZipFile.UseBackslash` kabul etme anahtarı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3f8a0-113">The following shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-in switch.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| <span data-ttu-id="3f8a0-114">Name</span><span class="sxs-lookup"><span data-stu-id="3f8a0-114">Name</span></span>    | <span data-ttu-id="3f8a0-115">Değer</span><span class="sxs-lookup"><span data-stu-id="3f8a0-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3f8a0-116">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3f8a0-116">Scope</span></span>   | <span data-ttu-id="3f8a0-117">Edge</span><span class="sxs-lookup"><span data-stu-id="3f8a0-117">Edge</span></span>        |
| <span data-ttu-id="3f8a0-118">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3f8a0-118">Version</span></span> | <span data-ttu-id="3f8a0-119">4.6.1</span><span class="sxs-lookup"><span data-stu-id="3f8a0-119">4.6.1</span></span>       |
| <span data-ttu-id="3f8a0-120">Tür</span><span class="sxs-lookup"><span data-stu-id="3f8a0-120">Type</span></span>    | <span data-ttu-id="3f8a0-121">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="3f8a0-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3f8a0-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3f8a0-122">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
