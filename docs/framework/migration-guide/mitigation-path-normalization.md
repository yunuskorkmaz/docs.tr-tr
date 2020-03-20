---
title: 'Azaltma: Yol Normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 61c8eec2043aa2fb9309ee6052e27fc2c91c6c6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181231"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="45c28-102">Azaltma: Yol Normalleştirme</span><span class="sxs-lookup"><span data-stu-id="45c28-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="45c28-103">.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak,.NET Framework'deki yol normalleştirmesi değişti.</span><span class="sxs-lookup"><span data-stu-id="45c28-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="45c28-104">Yol normalleştirme nedir?</span><span class="sxs-lookup"><span data-stu-id="45c28-104">What is path normalization?</span></span>  
 <span data-ttu-id="45c28-105">Bir yolu normalleştirmek, hedef işletim sistemindegeçerli bir yola uyacak şekilde bir yolu veya dosyayı tanımlayan dizeyi değiştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="45c28-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="45c28-106">Normalleştirme genellikle içerir:</span><span class="sxs-lookup"><span data-stu-id="45c28-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="45c28-107">Bileşen ve dizin ayırıcıları canonicalizing.</span><span class="sxs-lookup"><span data-stu-id="45c28-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="45c28-108">Geçerli dizini göreli bir yola uygulama.</span><span class="sxs-lookup"><span data-stu-id="45c28-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="45c28-109">Bir yolda göreli`.`dizinin ( ) veya`..`üst dizinin değerlendirilmesi.</span><span class="sxs-lookup"><span data-stu-id="45c28-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="45c28-110">Belirtilen karakterleri kırpma.</span><span class="sxs-lookup"><span data-stu-id="45c28-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="45c28-111">Değişiklikler</span><span class="sxs-lookup"><span data-stu-id="45c28-111">The changes</span></span>  
 <span data-ttu-id="45c28-112">.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak yol normalleştirmesi aşağıdaki şekillerde değişti:</span><span class="sxs-lookup"><span data-stu-id="45c28-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="45c28-113">Çalışma süresi, yolları normalleştirmek için işletim sisteminin [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) işlevine erteler.</span><span class="sxs-lookup"><span data-stu-id="45c28-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="45c28-114">Normalleştirme artık dizin kesimlerinin sonunda (dizin adının sonundaki boşluk gibi) kırpmayı içermez.</span><span class="sxs-lookup"><span data-stu-id="45c28-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="45c28-115">Aygıt yolu sözdizimini tam `\\.\` güven içinde ve mscorlib.dll'deki `\\?\`dosya G/Ç API'leri için destek.</span><span class="sxs-lookup"><span data-stu-id="45c28-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="45c28-116">Çalışma zamanı aygıt sözdizimi yollarını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="45c28-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="45c28-117">Alternatif veri akışlarına erişmek için aygıt sözdizimi kullanımı desteklenir.</span><span class="sxs-lookup"><span data-stu-id="45c28-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="45c28-118">Etki</span><span class="sxs-lookup"><span data-stu-id="45c28-118">Impact</span></span>  

<span data-ttu-id="45c28-119">.NET Framework 4.6.2 veya sonraki lerini hedefleyen uygulamalar için bu değişiklikler varsayılan olarak açıktır.</span><span class="sxs-lookup"><span data-stu-id="45c28-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="45c28-120">Yöntemlerin daha önce erişilemeyen yollara erişmesine izin verirken performansı artırmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="45c28-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="45c28-121">.NET Framework 4.6.1 ve önceki sürümleri hedefleyen ancak .NET Framework 4.6.2 veya daha sonra ları altında çalışan uygulamalar bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="45c28-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="45c28-122">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="45c28-122">Mitigation</span></span>  
 <span data-ttu-id="45c28-123">.NET Framework 4.6.2 veya daha sonrasını hedefleyen uygulamalar bu değişikliği devre dışı bırakıp [ \<](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının çalışma süresi>bölümüne aşağıdakileri ekleyerek eski normalleştirmeyi kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="45c28-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="45c28-124">.NET Framework 4.6.1 veya daha öncesini hedefleyen ancak .NET Framework 4.6.2 veya sonraki bölümlerinde çalışan uygulamalar, uygulamanın [ \<çalışma süresi>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satırı ekleyerek normalize yol değişikliklerini etkinleştirebilir .configuration dosyası:</span><span class="sxs-lookup"><span data-stu-id="45c28-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45c28-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45c28-125">See also</span></span>

- [<span data-ttu-id="45c28-126">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="45c28-126">Application compatibility</span></span>](application-compatibility.md)
