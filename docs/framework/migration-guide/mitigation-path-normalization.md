---
title: 'Risk azaltma: yol normalleştirme'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 1e7b540975b84320d099ca004df5b6a87aa60f6a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457892"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="08215-102">Risk azaltma: yol normalleştirme</span><span class="sxs-lookup"><span data-stu-id="08215-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="08215-103">Uygulamalarla başlayarak .NET Framework 4.6.2 hedefini hedefleyin .NET Framework yol normalleştirme değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="08215-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="08215-104">Yol normalleştirme nedir?</span><span class="sxs-lookup"><span data-stu-id="08215-104">What is path normalization?</span></span>  
 <span data-ttu-id="08215-105">Bir yolun normalleştirilmesi, bir yolu veya dosyayı tanımlayan dizeyi, hedef işletim sisteminde geçerli bir yola uygun olacak şekilde değiştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="08215-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="08215-106">Normalleştirme genellikle şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="08215-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="08215-107">Standart hale getirme bileşeni ve Dizin ayırıcıları.</span><span class="sxs-lookup"><span data-stu-id="08215-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="08215-108">Geçerli dizin göreli bir yola uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="08215-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="08215-109">Göreli dizin (`.`) veya üst dizin (`..`) bir yolda değerlendiriliyor.</span><span class="sxs-lookup"><span data-stu-id="08215-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="08215-110">Belirtilen karakterler kırpılırken.</span><span class="sxs-lookup"><span data-stu-id="08215-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="08215-111">Değişiklikler</span><span class="sxs-lookup"><span data-stu-id="08215-111">The changes</span></span>  
 <span data-ttu-id="08215-112">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, yol normalleştirme aşağıdaki yollarla değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="08215-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="08215-113">Çalışma zamanı, yolları normalleştirmek için işletim sisteminin [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) işlevine erteler.</span><span class="sxs-lookup"><span data-stu-id="08215-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="08215-114">Normalleştirme artık Dizin segmentlerinin bitmesini (Dizin adının sonundaki bir boşluk gibi) kırpmasını kapsar.</span><span class="sxs-lookup"><span data-stu-id="08215-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="08215-115">`\\.\` ve, mscorlib. dll ' deki dosya g/ç API 'Leri için `\\?\`dahil olmak üzere tam güvende cihaz yolu sözdizimi desteği.</span><span class="sxs-lookup"><span data-stu-id="08215-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="08215-116">Çalışma zamanı, cihaz sözdizimi yollarını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="08215-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="08215-117">Alternatif veri akışlarına erişmek için cihaz sözdiziminin kullanılması desteklenir.</span><span class="sxs-lookup"><span data-stu-id="08215-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="08215-118">Etki</span><span class="sxs-lookup"><span data-stu-id="08215-118">Impact</span></span>  

<span data-ttu-id="08215-119">.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar için bu değişiklikler varsayılan olarak açık.</span><span class="sxs-lookup"><span data-stu-id="08215-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="08215-120">Daha önce erişilemeyen yollara erişme yöntemlerine izin verirken performansı artırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08215-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="08215-121">.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="08215-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="08215-122">Azaltma</span><span class="sxs-lookup"><span data-stu-id="08215-122">Mitigation</span></span>  
 <span data-ttu-id="08215-123">.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve uygulama yapılandırma dosyasının [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdakileri ekleyerek eski normalleştirmeyi kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="08215-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
<span data-ttu-id="08215-124">.NET Framework 4.6.1 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar, uygulama. yapılandırma dosyasının [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satırı ekleyerek yol normalleştirmede yapılan değişiklikleri etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="08215-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08215-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08215-125">See also</span></span>

- [<span data-ttu-id="08215-126">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="08215-126">Application compatibility</span></span>](application-compatibility.md)
