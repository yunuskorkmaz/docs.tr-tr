---
title: 'Azaltma: ZipArchiveEntry.FullName Yol Ayırıcı'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 021d22e90ba39a4d01cf7d64588fab2d724b6640
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457725"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="86916-102">Azaltma: ZipArchiveEntry.FullName Yol Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="86916-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="86916-103">.NET Framework 4.6.1'i hedefleyen uygulamalardan başlayarak, <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özellikte kullanılan yol ayırıcısı .NET Framework'ün önceki sürümlerinde kullanılan ters eğik çizgiden ("/")\\ileri eğik çizgiye ("/") dönüşmüştür.</span><span class="sxs-lookup"><span data-stu-id="86916-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="86916-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType><xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> nesneler, yöntemin aşırı yüklerinden birini çağırarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="86916-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="86916-105">Etki</span><span class="sxs-lookup"><span data-stu-id="86916-105">Impact</span></span>  
 <span data-ttu-id="86916-106">Değişiklik, .NET uygulamasını 4.4.17.1 bölümüne uygun bir şekilde [getirir. ZIP Dosya Formatı Belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve sağlar. Windows olmayan sistemlerde sıkıştırılacak ZIP arşivleri.</span><span class="sxs-lookup"><span data-stu-id="86916-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="86916-107">Macintosh gibi Windows dışı işletim sistemlerinde .NET Framework'ün önceki bir sürümünü hedefleyen bir uygulama tarafından oluşturulan zip dosyasını sıkıştırmak dizin yapısını koruyamaz.</span><span class="sxs-lookup"><span data-stu-id="86916-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="86916-108">Örneğin, Macintosh'ta, dosya adı dizin yolunu, herhangi bir ters eğik çizgi ("\\") karakterle ve dosya adıyla birlikte birleştirir.</span><span class="sxs-lookup"><span data-stu-id="86916-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="86916-109">Sonuç olarak, sıkıştırılmış dosyaların dizin yapısı korunmaz.</span><span class="sxs-lookup"><span data-stu-id="86916-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="86916-110">Bu değişikliğin . .NET Framework <xref:System.IO> ad alanında API'ler tarafından Windows işletim sisteminde sıkıştırılan ZIP dosyaları en az düzeyde olmalıdır, çünkü bu API'ler yol\\ayırıcı karakteri olarak bir eğik çizgi ("/") veya ters eğik çizgi (" ") sorunsuz bir şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="86916-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="86916-111">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="86916-111">Mitigation</span></span>  
 <span data-ttu-id="86916-112">Bu davranış istenmiyorsa, uygulama yapılandırma dosyanızın [ \<çalışma>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne yapılandırma ayarı ekleyerek devre dışı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86916-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="86916-113">Aşağıda hem `<runtime>` bölümü hem de devre dışı bırakma anahtarı nı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="86916-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="86916-114">Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 ve sonraki sürümlerde çalışan uygulamalar, [ \<](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının çalışma zamanı>bölümüne yapılandırma ayarını ekleyerek bu davranışı seçebilir.</span><span class="sxs-lookup"><span data-stu-id="86916-114">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="86916-115">Aşağıdaki bölüm ve `<runtime>` opt-in anahtarı hem de gösterir.</span><span class="sxs-lookup"><span data-stu-id="86916-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86916-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86916-116">See also</span></span>

- [<span data-ttu-id="86916-117">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="86916-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="86916-118">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="86916-118">Application compatibility</span></span>](application-compatibility.md)
