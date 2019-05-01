---
title: 'Azaltma: ZipArchiveEntry.FullName yol ayırıcısı'
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
ms.openlocfilehash: eba871215f33e4d3b50054e9ceaa92be090d0143
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871117"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="ae80a-102">Azaltma: ZipArchiveEntry.FullName yol ayırıcısı</span><span class="sxs-lookup"><span data-stu-id="ae80a-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="ae80a-103">Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], kullanılan yolu ayırıcısı <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özelliği, ters eğik çizgiden değişti ("\\") eğik çizgi ("/") için .NET Framework'ün önceki sürümlerinde kullanılan.</span><span class="sxs-lookup"><span data-stu-id="ae80a-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="ae80a-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> nesneleri, aşırı yüklemelerini çağırarak oluşturulur <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ae80a-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ae80a-105">Etki</span><span class="sxs-lookup"><span data-stu-id="ae80a-105">Impact</span></span>  
 <span data-ttu-id="ae80a-106">Değişiklik 4.4.17.1 bölümünü ile uyumu .NET uygulamasına getirir [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve sağlar. Windows olmayan sistemlerde sıkıştırmasının açılması için ZIP arşivlerini.</span><span class="sxs-lookup"><span data-stu-id="ae80a-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="ae80a-107">Dizin yapısı korumak için Macintosh gibi Windows olmayan işletim sistemlerinde .NET Framework'ün önceki bir sürümü başarısız hedefleyen bir uygulama tarafından oluşturulan bir zip dosyası açılıyor.</span><span class="sxs-lookup"><span data-stu-id="ae80a-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="ae80a-108">Örneğin, bir dosya adı, dizin yolu bir eğik çizgi ile birlikte art arda ekler kümesini oluşturur Macintosh ("\\") karakteri ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="ae80a-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="ae80a-109">Sonuç olarak, açılan sıkıştırılmış dosyaların dizin yapısını korunmaz.</span><span class="sxs-lookup"><span data-stu-id="ae80a-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="ae80a-110">Bu değişiklik etkisini. Windows işletim sisteminde .NET Framework API'leri tarafından sıkıştırması ZIP dosyaları <xref:System.IO> bu API'leri bir eğik çizgi ("/") veya ters eğik çizgi sorunsuz bir şekilde işleyebilir beri ad alanı en az olmalıdır ("\\") olarak yol ayırıcı karakteri.</span><span class="sxs-lookup"><span data-stu-id="ae80a-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ae80a-111">Azaltma</span><span class="sxs-lookup"><span data-stu-id="ae80a-111">Mitigation</span></span>  
 <span data-ttu-id="ae80a-112">Bu davranış, istenmeyen ise, / için bir yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) , uygulama yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="ae80a-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="ae80a-113">Aşağıdaki her ikisini de gösteren `<runtime>` bölümü ve geri çevirme anahtar.</span><span class="sxs-lookup"><span data-stu-id="ae80a-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="ae80a-114">Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak üzerinde çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve sonraki sürümler kabul etme için bu davranışı için bir yapılandırma ayarı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümü Uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="ae80a-114">In addition, apps that target previous versions of the .NET Framework but are running on the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="ae80a-115">Aşağıdaki her ikisini de gösteren `<runtime>` bölümü ve katılım anahtar.</span><span class="sxs-lookup"><span data-stu-id="ae80a-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae80a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae80a-116">See also</span></span>

- [<span data-ttu-id="ae80a-117">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="ae80a-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="ae80a-118">4.6.1 uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="ae80a-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
