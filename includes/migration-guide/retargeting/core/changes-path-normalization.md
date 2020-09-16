---
ms.openlocfilehash: 7c4b9faf25853c1c7a546f06c329f6f153eef904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606938"
---
### <a name="changes-in-path-normalization"></a><span data-ttu-id="b19ba-101">Yol normalleştirmede değişiklikler</span><span class="sxs-lookup"><span data-stu-id="b19ba-101">Changes in path normalization</span></span>

#### <a name="details"></a><span data-ttu-id="b19ba-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b19ba-102">Details</span></span>

<span data-ttu-id="b19ba-103">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, çalışma zamanının yol normalleştirme yöntemi değişti. Bir yolun normalleştirilmesi, bir yolu veya dosyayı tanımlayan dizeyi, hedef işletim sisteminde geçerli bir yola uygun olacak şekilde değiştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="b19ba-103">Starting with apps that target the .NET Framework 4.6.2, the way in which the runtime normalizes paths has changed.Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="b19ba-104">Normalleştirme genellikle şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="b19ba-104">Normalization typically involves:</span></span>

- <span data-ttu-id="b19ba-105">Standart hale getirme bileşeni ve Dizin ayırıcıları.</span><span class="sxs-lookup"><span data-stu-id="b19ba-105">Canonicalizing component and directory separators.</span></span>
- <span data-ttu-id="b19ba-106">Geçerli dizin göreli bir yola uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="b19ba-106">Applying the current directory to a relative path.</span></span>
- <span data-ttu-id="b19ba-107">Göreli dizin (.) veya üst dizin (..) bir yolda değerlendiriliyor.</span><span class="sxs-lookup"><span data-stu-id="b19ba-107">Evaluating the relative directory (.) or the parent directory (..) in a path.</span></span>
- <span data-ttu-id="b19ba-108">Belirtilen karakterler kırpılırken.</span><span class="sxs-lookup"><span data-stu-id="b19ba-108">Trimming specified characters.</span></span>
<span data-ttu-id="b19ba-109">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, yol normalleştirmede aşağıdaki değişiklikler varsayılan olarak etkindir:</span><span class="sxs-lookup"><span data-stu-id="b19ba-109">Starting with apps that target the .NET Framework 4.6.2, the following changes in path normalization are enabled by default:</span></span>
  - <span data-ttu-id="b19ba-110">Çalışma zamanı, yolları normalleştirmek için işletim sisteminin [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) işlevine erteler.</span><span class="sxs-lookup"><span data-stu-id="b19ba-110">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) function to normalize paths.</span></span>
- <span data-ttu-id="b19ba-111">Normalleştirme artık Dizin segmentlerinin bitmesini (Dizin adının sonundaki bir boşluk gibi) kırpmasını kapsar.</span><span class="sxs-lookup"><span data-stu-id="b19ba-111">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>
- <span data-ttu-id="b19ba-112">`\\.\`mscorlib.dll ' deki dosya g/ç API 'leri için ve dahil olmak üzere tam güvende cihaz yolu söz dizimi desteği `\\?\` .</span><span class="sxs-lookup"><span data-stu-id="b19ba-112">Support for device path syntax in full trust, including `\\.\` and, for file I/O APIs in mscorlib.dll, `\\?\`.</span></span>
- <span data-ttu-id="b19ba-113">Çalışma zamanı, cihaz sözdizimi yollarını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="b19ba-113">The runtime does not validate device syntax paths.</span></span>
- <span data-ttu-id="b19ba-114">Alternatif veri akışlarına erişmek için cihaz sözdiziminin kullanılması desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b19ba-114">The use of device syntax to access alternate data streams is supported.</span></span>
<span data-ttu-id="b19ba-115">Bu değişiklikler, daha önce erişilemeyen yollara erişme yöntemlerinin kullanılmasına izin verirken performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="b19ba-115">These changes improve performance while allowing methods to access previously inaccessible paths.</span></span> <span data-ttu-id="b19ba-116">.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="b19ba-116">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b19ba-117">Öneri</span><span class="sxs-lookup"><span data-stu-id="b19ba-117">Suggestion</span></span>

<span data-ttu-id="b19ba-118">.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdakini ekleyerek eski normalleştirmeyi kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="b19ba-118">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

<span data-ttu-id="b19ba-119">.NET Framework 4.6.1 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar, `<runtime>` uygulama. yapılandırma dosyasının bölümüne aşağıdaki satırı ekleyerek yol normalleştirmede yapılan değişiklikleri etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="b19ba-119">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| <span data-ttu-id="b19ba-120">Name</span><span class="sxs-lookup"><span data-stu-id="b19ba-120">Name</span></span>    | <span data-ttu-id="b19ba-121">Değer</span><span class="sxs-lookup"><span data-stu-id="b19ba-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b19ba-122">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b19ba-122">Scope</span></span>   | <span data-ttu-id="b19ba-123">İkincil</span><span class="sxs-lookup"><span data-stu-id="b19ba-123">Minor</span></span>       |
| <span data-ttu-id="b19ba-124">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b19ba-124">Version</span></span> | <span data-ttu-id="b19ba-125">4.6.2</span><span class="sxs-lookup"><span data-stu-id="b19ba-125">4.6.2</span></span>       |
| <span data-ttu-id="b19ba-126">Tür</span><span class="sxs-lookup"><span data-stu-id="b19ba-126">Type</span></span>    | <span data-ttu-id="b19ba-127">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="b19ba-127">Retargeting</span></span> |
