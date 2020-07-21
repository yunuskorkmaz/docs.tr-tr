---
title: 'Azaltma: Ürün Sürümü Oluşturma'
description: Bu makalede, önceki sürümlerden .NET Framework 4,6 ve üzeri ürün sürümü oluşturma işlemlerinin nasıl değiştiği hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 442c06446e763758d3a150ee9ff884a616541c07
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475404"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="359d3-103">Azaltma: Ürün Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="359d3-103">Mitigation: Product Versioning</span></span>

<span data-ttu-id="359d3-104">.NET Framework 4,6 ve üzeri sürümlerde, ürün sürümü oluşturma işlemi önceki .NET Framework sürümlerinden (.NET Framework 4, 4,5, 4.5.1 ve 4.5.2) değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="359d3-104">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="359d3-105">Ürün sürümü oluşturma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="359d3-105">Product versioning changes</span></span>

<span data-ttu-id="359d3-106">Ayrıntılı değişiklikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="359d3-106">The following are the detailed changes:</span></span>

- <span data-ttu-id="359d3-107">Anahtardaki girdinin değeri, `Version` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` `4.6.` .NET Framework 4,6 ve noktası sürümleri için *xxxxx* , `4.7.` .NET Framework 4,7 için *xxxxx* olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="359d3-107">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="359d3-108">.NET Framework 4,5, 4.5.1 ve 4.5.2 ' de, `4.5.` *xxxxx*biçiminde vardı.</span><span class="sxs-lookup"><span data-stu-id="359d3-108">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="359d3-109">.NET Framework dosyaları için dosya ve ürün sürümü oluşturma, `4.0.30319.x` `4.6.X.0` .NET Framework 4,6 ve noktası sürümleri için ve `4.7.X.0` .NET Framework 4,7 ve noktası sürümleri için için önceki sürüm oluşturma düzeninden değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="359d3-109">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="359d3-110">Bir dosyaya sağ tıkladıktan sonra dosyanın **özelliklerini** görüntülerken bu yeni değerleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="359d3-110">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="359d3-111"><xref:System.Reflection.AssemblyFileVersionAttribute> <xref:System.Reflection.AssemblyInformationalVersionAttribute> Yönetilen derlemelerin ve özniteliklerinin <xref:System.Version> `4.6.X.0` .NET Framework 4,6 ve nokta sürümleri için ve .NET Framework 4,7 için biçimde değerleri vardır `4.7.X.0` .</span><span class="sxs-lookup"><span data-stu-id="359d3-111">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="359d3-112">.NET Framework 4,6 ' den başlayarak, <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği sabit sürüm dizesini döndürür `4.0.30319.42000` .</span><span class="sxs-lookup"><span data-stu-id="359d3-112">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="359d3-113">.NET Framework 4, 4,5, 4.5.1 ve 4.5.2 ' de, sürüm dizelerini `4.0.30319.xxxxx` `xxxxx` 42000 ' den daha düşük olan biçimde döndürür (örneğin, "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="359d3-113">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="359d3-114">Özellik üzerinde herhangi bir yeni bağımlılığı alan uygulama kodunu önermiyoruz <xref:System.Environment.Version%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="359d3-114">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="359d3-115">Ürün sürümü oluşturma değişikliklerini işleme</span><span class="sxs-lookup"><span data-stu-id="359d3-115">Handling the product versioning changes</span></span>

<span data-ttu-id="359d3-116">Genel olarak, uygulamalar .NET Framework çalışma zamanı sürümü ve yükleme dizini gibi şeyleri tespit etmek için önerilen tekniklerin üzerine bağımlıdır:</span><span class="sxs-lookup"><span data-stu-id="359d3-116">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="359d3-117">.NET Framework çalışma zamanı sürümünü algılamak için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="359d3-117">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="359d3-118">.NET Framework için yükleme yolunu öğrenmek için, `InstallPath` anahtardaki girdinin değerini kullanın `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` .</span><span class="sxs-lookup"><span data-stu-id="359d3-118">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="359d3-119">Alt anahtar adı `NET Framework Setup` değil, `.NET Framework Setup` .</span><span class="sxs-lookup"><span data-stu-id="359d3-119">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="359d3-120">.NET Framework ortak dil çalışma zamanının dizin yolunu öğrenmek için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="359d3-120">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="359d3-121">CLR sürümünü almak için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="359d3-121">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="359d3-122">.NET Framework 4 ve nokta sürümleri (.NET Framework 4,5, 4.5.1, 4.5.2 ve .NET Framework 4,6, 4.6.1, 4.6.2 ve 4,7) için, dizeyi döndürür `v4.0.30319` .</span><span class="sxs-lookup"><span data-stu-id="359d3-122">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="359d3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="359d3-123">See also</span></span>

- [<span data-ttu-id="359d3-124">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="359d3-124">Application compatibility</span></span>](application-compatibility.md)
