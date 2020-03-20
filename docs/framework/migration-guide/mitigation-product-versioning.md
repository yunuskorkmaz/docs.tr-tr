---
title: 'Azaltma: Ürün Sürümü Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457804"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="44dce-102">Azaltma: Ürün Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="44dce-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="44dce-103">.NET Framework 4.6 ve sonraki sürümlerde, ürün sürümü .NET Framework'ün önceki sürümlerinden (.NET Framework 4, 4.5, 4.5.1 ve 4.5.2) değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="44dce-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="44dce-104">Ürün sürüm değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="44dce-104">Product versioning changes</span></span>

<span data-ttu-id="44dce-105">Ayrıntılı değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="44dce-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="44dce-106">`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` Anahtardaki `Version` girişin değeri .NET `4.6.`Framework 4.6 ve onun puan sürümleri için *xxxxx* ve `4.7.`.NET Framework 4.7 için *xxxxx* olarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="44dce-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="44dce-107">.NET Framework 4.5, 4.5.1 ve 4.5.2,, `4.5.`bu biçimi *xxxxx*vardı.</span><span class="sxs-lookup"><span data-stu-id="44dce-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="44dce-108">.NET Framework dosyalarının dosya ve ürün sürümü, .NET `4.0.30319.x` Framework `4.6.X.0` 4.6 ve onun nokta sürümleri için `4.7.X.0` önceki sürüm şemasından ,.NET Framework 4.7 ve puan sürümlerine dönüşmüştür.</span><span class="sxs-lookup"><span data-stu-id="44dce-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="44dce-109">Bir dosyaya sağ tıkladıktan sonra dosyanın **Özelliklerini** görüntülediğinizde bu yeni değerleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44dce-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="44dce-110">Yönetilen <xref:System.Reflection.AssemblyFileVersionAttribute> <xref:System.Reflection.AssemblyInformationalVersionAttribute> derlemelerin öznitelikleri <xref:System.Version> ,NET Framework `4.6.X.0` 4.6 ve onun nokta sürümleri ve `4.7.X.0` .NET Framework 4.7 için formda değerlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="44dce-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="44dce-111">.NET Framework 4.6 ile <xref:System.Environment.Version%2A?displayProperty=nameWithType> başlayarak, özellik `4.0.30319.42000`sabit sürüm dizesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="44dce-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="44dce-112">.NET Framework 4, 4.5, 4.5.1 ve 4.5.2'de sürüm dizelerini 42000'den az olan `4.0.30319.xxxxx` `xxxxx` biçimde döndürür (örneğin, "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="44dce-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="44dce-113">Uygulama kodunun özelliğe yeni bir bağımlılık uygulamanızı önermediğimizi <xref:System.Environment.Version%2A?displayProperty=nameWithType> unutmayın.</span><span class="sxs-lookup"><span data-stu-id="44dce-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="44dce-114">Ürün sürüm değişikliklerini işleme</span><span class="sxs-lookup"><span data-stu-id="44dce-114">Handling the product versioning changes</span></span>

<span data-ttu-id="44dce-115">Genel olarak, uygulamalar .NET Framework'ün çalışma zamanı sürümü ve yükleme dizini gibi şeyleri algılamak için önerilen tekniklere bağlı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="44dce-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="44dce-116">.NET Framework'ün çalışma zamanı sürümünü algılamak için [bkz: Hangi .NET Framework Sürümlerinin Yüklü olduğunu belirleyin.](how-to-determine-which-versions-are-installed.md)</span><span class="sxs-lookup"><span data-stu-id="44dce-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="44dce-117">.NET Framework için yükleme yolunu belirlemek `InstallPath` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` için, anahtardaki giriş değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="44dce-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="44dce-118">Alt anahtar adı `NET Framework Setup`, `.NET Framework Setup`değil.</span><span class="sxs-lookup"><span data-stu-id="44dce-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="44dce-119">.NET Framework ortak dil çalışma zamanına giden dizin <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yolunu belirlemek için yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="44dce-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="44dce-120">CLR sürümünü almak için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="44dce-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="44dce-121">.NET Framework 4 ve onun nokta sürümleri için (.NET Framework 4.5, 4.5.1, 4.5.2 ve .NET Framework 4.6, 4.6.1, `v4.0.30319`4.6.2 ve 4.7) dizesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="44dce-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="44dce-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44dce-122">See also</span></span>

- [<span data-ttu-id="44dce-123">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="44dce-123">Application compatibility</span></span>](application-compatibility.md)
