---
title: 'Azaltma: Yol normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1c704113c8e05e493cdb3ef24f6376ab54b1cb
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251121"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="2f4f7-102">Azaltma: Yol normalleştirme</span><span class="sxs-lookup"><span data-stu-id="2f4f7-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="2f4f7-103">Hedef .NET Framework 4.6.2 uygulamaları ile başlayarak, .NET Framework'teki yolu normalleştirme değişti.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="2f4f7-104">Yol normalleştirme nedir?</span><span class="sxs-lookup"><span data-stu-id="2f4f7-104">What is path normalization?</span></span>  
 <span data-ttu-id="2f4f7-105">Bir yol normalleştirme, böylece geçerli bir yol hedef işletim sisteminde uyan bir yol veya dosya tanımlayan dize değiştirme içerir.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="2f4f7-106">Normalleştirme genellikle içerir:</span><span class="sxs-lookup"><span data-stu-id="2f4f7-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="2f4f7-107">Bileşen ve dizin ayırıcı standart hale getirme.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="2f4f7-108">Geçerli dizine göreli bir yol uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="2f4f7-109">Göreli dizini değerlendirme (`.`) veya bir üst dizin (`..`) bir yolda.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="2f4f7-110">Karakterleri kırpma belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="2f4f7-111">Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="2f4f7-111">The changes</span></span>  
 <span data-ttu-id="2f4f7-112">.NET Framework 4.6.2'yi hedefleyen uygulamalar ile başlayarak, aşağıdaki yollarla yolu normalleştirme değişmiştir:</span><span class="sxs-lookup"><span data-stu-id="2f4f7-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="2f4f7-113">İşletim sistemi için çalışma zamanı erteler [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) yolları'leri normalleştirmek için işlevi.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="2f4f7-114">Artık normalleştirme directory Segment (örneğin, bir dizin adı, sonunda boşluk) sonuna kırpma içerir.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="2f4f7-115">Cihaz yolu sözdizimi tam güven için destek dahil olmak üzere `\\.\` ve dosya g/ç API'leri mscorlib.dll için `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="2f4f7-116">Çalışma zamanı, cihaz sözdizimi yolları doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="2f4f7-117">Alternatif veri akışları erişmek için cihaz sözdizimi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="2f4f7-118">Etki</span><span class="sxs-lookup"><span data-stu-id="2f4f7-118">Impact</span></span>  

<span data-ttu-id="2f4f7-119">.NET Framework 4.6.2'yi hedefleyen uygulamalar için veya daha sonra bu değişiklikleri varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="2f4f7-120">Daha önce erişilemeyen yolları erişmek yöntemleri sağlarken performansı.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="2f4f7-121">.NET Framework 4.6.1 ve önceki sürümleri hedefleyen, ancak .NET Framework 4.6.2 altında çalışan ya da üzeri olan uygulamalar, bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="2f4f7-122">Azaltma</span><span class="sxs-lookup"><span data-stu-id="2f4f7-122">Mitigation</span></span>  
 <span data-ttu-id="2f4f7-123">Daha sonra bu dışında seçebilirsiniz veya .NET Framework 4.6.2'yi hedefleyen uygulamalar değiştirin ve aşağıdaki ekleyerek eski normalleştirme kullanın [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyası bölümünü:</span><span class="sxs-lookup"><span data-stu-id="2f4f7-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
<span data-ttu-id="2f4f7-124">.NET Framework 4.6.1 veya önceki ancak hedefleyen uygulamaları .NET Framework 4.6.2 üzerinde çalışıyor veya aşağıdaki satırı ekleyerek yolu normalleştirme değişiklikleri daha sonra etkinleştirebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümü uygulama .configuration dosyası:</span><span class="sxs-lookup"><span data-stu-id="2f4f7-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f4f7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f4f7-125">See also</span></span>

- [<span data-ttu-id="2f4f7-126">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="2f4f7-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
