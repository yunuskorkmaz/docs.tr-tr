---
title: 'Azaltma: Yolu normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36433dcce1e47b329f5407e86ce3923a44cb6444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389546"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="86bd6-102">Azaltma: Yolu normalleştirme</span><span class="sxs-lookup"><span data-stu-id="86bd6-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="86bd6-103">Hedef uygulamalarla başlangıç [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], .NET Framework'teki yolu normalleştirme değişti.</span><span class="sxs-lookup"><span data-stu-id="86bd6-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="86bd6-104">Yol normalleştirme nedir?</span><span class="sxs-lookup"><span data-stu-id="86bd6-104">What is path normalization?</span></span>  
 <span data-ttu-id="86bd6-105">Bir yol normalleştirme bir yol veya dosya tanımlar ve böylece geçerli bir yol hedef işletim sisteminde uyacağını dizesini değiştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="86bd6-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="86bd6-106">Normalleştirme genellikle içerir:</span><span class="sxs-lookup"><span data-stu-id="86bd6-106">Normalization typically involves:</span></span>  
  
-   <span data-ttu-id="86bd6-107">Bileşen ve dizin ayırıcı standart hale getirme.</span><span class="sxs-lookup"><span data-stu-id="86bd6-107">Canonicalizing component and directory separators.</span></span>  
  
-   <span data-ttu-id="86bd6-108">Geçerli dizine göreli bir yol uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="86bd6-108">Applying the current directory to a relative path.</span></span>  
  
-   <span data-ttu-id="86bd6-109">Göreli directory değerlendirme (`.`) ya da üst dizini (`..`) bir yolda.</span><span class="sxs-lookup"><span data-stu-id="86bd6-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
-   <span data-ttu-id="86bd6-110">Kırpma karakterleri belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="86bd6-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="86bd6-111">Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="86bd6-111">The changes</span></span>  
 <span data-ttu-id="86bd6-112">Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], yol normalleştirme aşağıdaki yollarla değişti:</span><span class="sxs-lookup"><span data-stu-id="86bd6-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="86bd6-113">İşletim sistemi için çalışma zamanı erteler [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) yolları normalleştirmek için işlevi.</span><span class="sxs-lookup"><span data-stu-id="86bd6-113">The runtime defers to the operating system's [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) function to normalize paths.</span></span>  
  
-   <span data-ttu-id="86bd6-114">Normalleştirme artık dizin Segment (örneğin, bir dizin adının sonunda boşluk) sonuna kırpma içerir.</span><span class="sxs-lookup"><span data-stu-id="86bd6-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
-   <span data-ttu-id="86bd6-115">Tam güven yolu sözdiziminde cihaz için destek dahil olmak üzere `\\.\` ve mscorlib.dll, g/ç API'leri dosyasında `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="86bd6-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
-   <span data-ttu-id="86bd6-116">Çalışma zamanı aygıt sözdizimi yolları doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="86bd6-116">The runtime does not validate device syntax paths.</span></span>  
  
-   <span data-ttu-id="86bd6-117">Alternatif veri akışları erişmek için cihaz sözdizimi kullanımı desteklenir.</span><span class="sxs-lookup"><span data-stu-id="86bd6-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="86bd6-118">Etki</span><span class="sxs-lookup"><span data-stu-id="86bd6-118">Impact</span></span>  
 <span data-ttu-id="86bd6-119">Hedef uygulamalar için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra bu değişiklikleri varsayılan olarak açıktır.</span><span class="sxs-lookup"><span data-stu-id="86bd6-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="86bd6-120">Daha önce erişilemez yollara erişmek yöntemler verirken performansı.</span><span class="sxs-lookup"><span data-stu-id="86bd6-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="86bd6-121">Hedef uygulamaları [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki sürümleri ancak olan çalışırken [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="86bd6-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="86bd6-122">Azaltma</span><span class="sxs-lookup"><span data-stu-id="86bd6-122">Mitigation</span></span>  
 <span data-ttu-id="86bd6-123">Hedef uygulamaları [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya daha sonra dışında bu değişikliği kabul ve eski normalleştirme aşağıdakileri ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının:</span><span class="sxs-lookup"><span data-stu-id="86bd6-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="86bd6-124">Hedef uygulamaları [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya önceki ancak üzerinde çalışan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] veya aşağıdaki satırı ekleyerek yolu normalleştirme değişiklikleri daha sonra etkinleştirebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama bölümü. yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="86bd6-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86bd6-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86bd6-125">See Also</span></span>  
 [<span data-ttu-id="86bd6-126">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="86bd6-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
