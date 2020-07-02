---
ms.openlocfilehash: 04c4fb4c8e9da8c58a5e26f78a7b13aa6a0df4a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614690"
---
### <a name="changes-in-path-normalization"></a><span data-ttu-id="69dc8-101">Yol normalleştirmede değişiklikler</span><span class="sxs-lookup"><span data-stu-id="69dc8-101">Changes in path normalization</span></span>

#### <a name="details"></a><span data-ttu-id="69dc8-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="69dc8-102">Details</span></span>

<span data-ttu-id="69dc8-103">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, çalışma zamanının yol normalleştirme yöntemi değişti. Bir yolun normalleştirilmesi, bir yolu veya dosyayı tanımlayan dizeyi, hedef işletim sisteminde geçerli bir yola uygun olacak şekilde değiştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="69dc8-103">Starting with apps that target the .NET Framework 4.6.2, the way in which the runtime normalizes paths has changed.Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="69dc8-104">Normalleştirme genellikle şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="69dc8-104">Normalization typically involves:</span></span>

- <span data-ttu-id="69dc8-105">Standart hale getirme bileşeni ve Dizin ayırıcıları.</span><span class="sxs-lookup"><span data-stu-id="69dc8-105">Canonicalizing component and directory separators.</span></span>
- <span data-ttu-id="69dc8-106">Geçerli dizin göreli bir yola uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="69dc8-106">Applying the current directory to a relative path.</span></span>
- <span data-ttu-id="69dc8-107">Göreli dizin (.) veya üst dizin (..) bir yolda değerlendiriliyor.</span><span class="sxs-lookup"><span data-stu-id="69dc8-107">Evaluating the relative directory (.) or the parent directory (..) in a path.</span></span>
- <span data-ttu-id="69dc8-108">Belirtilen karakterler kırpılırken.</span><span class="sxs-lookup"><span data-stu-id="69dc8-108">Trimming specified characters.</span></span>
<span data-ttu-id="69dc8-109">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, yol normalleştirmede aşağıdaki değişiklikler varsayılan olarak etkindir:</span><span class="sxs-lookup"><span data-stu-id="69dc8-109">Starting with apps that target the .NET Framework 4.6.2, the following changes in path normalization are enabled by default:</span></span>
  - <span data-ttu-id="69dc8-110">Çalışma zamanı, yolları normalleştirmek için işletim sisteminin [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) işlevine erteler.</span><span class="sxs-lookup"><span data-stu-id="69dc8-110">The runtime defers to the operating system's [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) function to normalize paths.</span></span>
- <span data-ttu-id="69dc8-111">Normalleştirme artık Dizin segmentlerinin bitmesini (Dizin adının sonundaki bir boşluk gibi) kırpmasını kapsar.</span><span class="sxs-lookup"><span data-stu-id="69dc8-111">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>
- <span data-ttu-id="69dc8-112">`\\.\`mscorlib.dll ' deki dosya g/ç API 'leri için ve dahil olmak üzere tam güvende cihaz yolu söz dizimi desteği `\\?\` .</span><span class="sxs-lookup"><span data-stu-id="69dc8-112">Support for device path syntax in full trust, including `\\.\` and, for file I/O APIs in mscorlib.dll, `\\?\`.</span></span>
- <span data-ttu-id="69dc8-113">Çalışma zamanı, cihaz sözdizimi yollarını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="69dc8-113">The runtime does not validate device syntax paths.</span></span>
- <span data-ttu-id="69dc8-114">Alternatif veri akışlarına erişmek için cihaz sözdiziminin kullanılması desteklenir.</span><span class="sxs-lookup"><span data-stu-id="69dc8-114">The use of device syntax to access alternate data streams is supported.</span></span>
<span data-ttu-id="69dc8-115">Bu değişiklikler, daha önce erişilemeyen yollara erişme yöntemlerinin kullanılmasına izin verirken performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="69dc8-115">These changes improve performance while allowing methods to access previously inaccessible paths.</span></span> <span data-ttu-id="69dc8-116">.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="69dc8-116">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="69dc8-117">Öneri</span><span class="sxs-lookup"><span data-stu-id="69dc8-117">Suggestion</span></span>

<span data-ttu-id="69dc8-118">.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdakini ekleyerek eski normalleştirmeyi kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="69dc8-118">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

<span data-ttu-id="69dc8-119">.NET Framework 4.6.1 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar, `<runtime>` uygulama. yapılandırma dosyasının bölümüne aşağıdaki satırı ekleyerek yol normalleştirmede yapılan değişiklikleri etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="69dc8-119">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| <span data-ttu-id="69dc8-120">Name</span><span class="sxs-lookup"><span data-stu-id="69dc8-120">Name</span></span>    | <span data-ttu-id="69dc8-121">Değer</span><span class="sxs-lookup"><span data-stu-id="69dc8-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="69dc8-122">Kapsam</span><span class="sxs-lookup"><span data-stu-id="69dc8-122">Scope</span></span>   | <span data-ttu-id="69dc8-123">İkincil</span><span class="sxs-lookup"><span data-stu-id="69dc8-123">Minor</span></span>       |
| <span data-ttu-id="69dc8-124">Sürüm</span><span class="sxs-lookup"><span data-stu-id="69dc8-124">Version</span></span> | <span data-ttu-id="69dc8-125">4.6.2</span><span class="sxs-lookup"><span data-stu-id="69dc8-125">4.6.2</span></span>       |
| <span data-ttu-id="69dc8-126">Tür</span><span class="sxs-lookup"><span data-stu-id="69dc8-126">Type</span></span>    | <span data-ttu-id="69dc8-127">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="69dc8-127">Retargeting</span></span> |
