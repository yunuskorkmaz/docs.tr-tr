---
title: 'Azaltma: Yol normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37241dd666a5d10eeb35bcbb4c9e09a5bc56f620
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871520"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="f151b-102">Azaltma: Yol normalleştirme</span><span class="sxs-lookup"><span data-stu-id="f151b-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="f151b-103">Hedef uygulama ile başlangıç [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], .NET Framework'teki yolu normalleştirme değişti.</span><span class="sxs-lookup"><span data-stu-id="f151b-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="f151b-104">Yol normalleştirme nedir?</span><span class="sxs-lookup"><span data-stu-id="f151b-104">What is path normalization?</span></span>  
 <span data-ttu-id="f151b-105">Bir yol normalleştirme, böylece geçerli bir yol hedef işletim sisteminde uyan bir yol veya dosya tanımlayan dize değiştirme içerir.</span><span class="sxs-lookup"><span data-stu-id="f151b-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="f151b-106">Normalleştirme genellikle içerir:</span><span class="sxs-lookup"><span data-stu-id="f151b-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="f151b-107">Bileşen ve dizin ayırıcı standart hale getirme.</span><span class="sxs-lookup"><span data-stu-id="f151b-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="f151b-108">Geçerli dizine göreli bir yol uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="f151b-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="f151b-109">Göreli dizini değerlendirme (`.`) veya bir üst dizin (`..`) bir yolda.</span><span class="sxs-lookup"><span data-stu-id="f151b-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="f151b-110">Karakterleri kırpma belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="f151b-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="f151b-111">Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f151b-111">The changes</span></span>  
 <span data-ttu-id="f151b-112">Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], yol normalleştirme aşağıdaki yollarla değişmiştir:</span><span class="sxs-lookup"><span data-stu-id="f151b-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="f151b-113">İşletim sistemi için çalışma zamanı erteler [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) yolları'leri normalleştirmek için işlevi.</span><span class="sxs-lookup"><span data-stu-id="f151b-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="f151b-114">Artık normalleştirme directory Segment (örneğin, bir dizin adı, sonunda boşluk) sonuna kırpma içerir.</span><span class="sxs-lookup"><span data-stu-id="f151b-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="f151b-115">Cihaz yolu sözdizimi tam güven için destek dahil olmak üzere `\\.\` ve dosya g/ç API'leri mscorlib.dll için `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="f151b-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="f151b-116">Çalışma zamanı, cihaz sözdizimi yolları doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="f151b-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="f151b-117">Alternatif veri akışları erişmek için cihaz sözdizimi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="f151b-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f151b-118">Etki</span><span class="sxs-lookup"><span data-stu-id="f151b-118">Impact</span></span>  
 <span data-ttu-id="f151b-119">Hedefleyen uygulamalar için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra bu değişiklikleri varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="f151b-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="f151b-120">Daha önce erişilemeyen yolları erişmek yöntemleri sağlarken performansı.</span><span class="sxs-lookup"><span data-stu-id="f151b-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="f151b-121">Hedefleyen uygulamaları [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki sürümleri ancak bunlar çalışırken [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="f151b-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f151b-122">Azaltma</span><span class="sxs-lookup"><span data-stu-id="f151b-122">Mitigation</span></span>  
 <span data-ttu-id="f151b-123">Hedefleyen uygulamaları [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra dışında bu değişikliği kabul ve eski normalleştirme aşağıdakileri ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyası bölümünü:</span><span class="sxs-lookup"><span data-stu-id="f151b-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="f151b-124">Hedefleyen uygulamaları [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya önceki ancak üzerinde çalışan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya aşağıdaki satırı ekleyerek yolu normalleştirme değişiklikleri daha sonra etkinleştirebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama bölümü. yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="f151b-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f151b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f151b-125">See also</span></span>

- [<span data-ttu-id="f151b-126">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f151b-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
