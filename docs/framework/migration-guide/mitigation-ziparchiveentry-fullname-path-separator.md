---
title: Mayı ZipArchiveEntry. FullName yol ayırıcısı
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b97436ca2f81fea139689c7c2c2348718827b90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778856"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="32c17-102">Mayı ZipArchiveEntry. FullName yol ayırıcısı</span><span class="sxs-lookup"><span data-stu-id="32c17-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="32c17-103">.NET Framework 4.6.1 ' i hedefleyen uygulamalarla başlayarak, <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özellikte kullanılan yol ayırıcısı, .NET Framework önceki sürümlerinde kullanılan ters\\eğik çizgiyle ("") ("/") değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32c17-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="32c17-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>nesneler, <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> yönteminin aşırı yüklerinden biri çağırarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="32c17-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="32c17-105">Etki</span><span class="sxs-lookup"><span data-stu-id="32c17-105">Impact</span></span>  
 <span data-ttu-id="32c17-106">Bu değişiklik, .NET uygulamasını konusunun Bölüm 4.4.17.1 ile uyum sağlar [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve izin verir. ZIP arşivleri Windows dışı sistemlerde açılacak.</span><span class="sxs-lookup"><span data-stu-id="32c17-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="32c17-107">Macintosh gibi Windows dışı işletim sistemlerinde .NET Framework önceki bir sürümünü hedefleyen bir uygulama tarafından oluşturulan bir ZIP dosyasını açma işlemi, dizin yapısını koruyamaz.</span><span class="sxs-lookup"><span data-stu-id="32c17-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="32c17-108">Örneğin, Macintosh üzerinde, dosya adı dizin yolunu, herhangi bir ters eğik çizgi ("\\") karakteri ve dosya adıyla birleştiren bir dosya kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="32c17-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="32c17-109">Sonuç olarak, açılan dosyaların dizin yapısı korunmaz.</span><span class="sxs-lookup"><span data-stu-id="32c17-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="32c17-110">Bu değişikliğin üzerinde etkisi. Windows işletim sisteminde .NET Framework <xref:System.IO> ad alanındaki API 'ler tarafından açılan ZIP dosyaları en düşük düzeyde olmalıdır, çünkü bu API 'ler yol ayırıcı karakteri olarak eğik çizgi ("/") veya ters eğik çizgi ("\\") sorunsuzca işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="32c17-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="32c17-111">Azaltma</span><span class="sxs-lookup"><span data-stu-id="32c17-111">Mitigation</span></span>  
 <span data-ttu-id="32c17-112">Bu davranış istenmeyen bir durum ise, uygulama yapılandırma dosyanızın [ \<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne bir yapılandırma ayarı ekleyerek devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32c17-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="32c17-113">Aşağıda hem `<runtime>` bölümü hem de geri çevirme anahtarı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="32c17-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="32c17-114">Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 ve sonraki sürümlerde çalışan uygulamalar, uygulamanın [ \<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne bir yapılandırma ayarı ekleyerek bu davranışı kabul edebilir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="32c17-114">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="32c17-115">Aşağıda hem `<runtime>` bölümü hem de kabul etme anahtarı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="32c17-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32c17-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32c17-116">See also</span></span>

- [<span data-ttu-id="32c17-117">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="32c17-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="32c17-118">4.6.1 'de uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="32c17-118">Application Compatibility in 4.6.1</span></span>](application-compatibility-in-the-net-framework-4-6-1.md)
