---
title: 'Risk azaltma: ZipArchiveEntry. FullName yol ayırıcısı'
description: ZipArchiveEntry. FullName özelliği için yol ayırıcısının, .NET Framework 4.6.1 hedeflenen uygulamalarla başlayarak nasıl değiştiğini öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 8cd6362038ce0548681f3d3b44724f3ef9ff62cb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475300"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="ff9b1-103">Risk azaltma: ZipArchiveEntry. FullName yol ayırıcısı</span><span class="sxs-lookup"><span data-stu-id="ff9b1-103">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="ff9b1-104">.NET Framework 4.6.1 ' i hedefleyen uygulamalarla başlayarak, özellikte kullanılan yol ayırıcısı, <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> \\ önceki .NET Framework sürümlerinde kullanılan ters eğik çizgiyle ("") ("/") değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-104">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="ff9b1-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>nesneler, yönteminin aşırı yüklerinden biri çağırarak oluşturulur <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ff9b1-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ff9b1-106">Etki</span><span class="sxs-lookup"><span data-stu-id="ff9b1-106">Impact</span></span>  
 <span data-ttu-id="ff9b1-107">Bu değişiklik, .NET uygulamasını konusunun Bölüm 4.4.17.1 ile uyum sağlar [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve izin verir. ZIP arşivleri Windows dışı sistemlerde açılacak.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-107">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="ff9b1-108">MacOS gibi Windows dışı işletim sistemlerinde .NET Framework önceki bir sürümünü hedefleyen, dizin yapısını koruyamayan bir uygulama tarafından oluşturulan bir zip dosyasını açma işlemi başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-108">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="ff9b1-109">Örneğin, MacOS 'ta dosya adı dizin yolunu, herhangi bir ters eğik çizgi (" \\ ") karakterini ve dosya adını birleştiren bir dosya kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-109">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="ff9b1-110">Sonuç olarak, açılan dosyaların dizin yapısı korunmaz.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-110">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="ff9b1-111">Bu değişikliğin üzerinde etkisi. <xref:System.IO>Bu API 'ler, yol ayırıcı karakteri olarak eğik çizgi ("/") veya ters eğik çizgi ("") ile sorunsuz bir şekilde işleyebildiğinden, Windows işletim sisteminde .NET Framework API 'ler tarafından AÇıLAN ZIP dosyaları en az olmalıdır \\ .</span><span class="sxs-lookup"><span data-stu-id="ff9b1-111">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ff9b1-112">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="ff9b1-112">Mitigation</span></span>  
 <span data-ttu-id="ff9b1-113">Bu davranış istenmeyen bir durum ise, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyanızın bölümüne bir yapılandırma ayarı ekleyerek devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-113">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="ff9b1-114">Aşağıda hem `<runtime>` bölümü hem de geri çevirme anahtarı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-114">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="ff9b1-115">Ayrıca, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 ve sonraki sürümlerde çalışan uygulamalar, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının bölümüne bir yapılandırma ayarı ekleyerek bu davranışı kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-115">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="ff9b1-116">Aşağıda hem `<runtime>` bölümü hem de kabul etme anahtarı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-116">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff9b1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff9b1-117">See also</span></span>

- [<span data-ttu-id="ff9b1-118">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="ff9b1-118">Application compatibility</span></span>](application-compatibility.md)
