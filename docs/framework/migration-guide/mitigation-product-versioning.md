---
title: Mayı Ürün sürümü oluşturma
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91db9d8c6fccf75bc9025a9487517e8c55d016cc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779215"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="778e0-102">Mayı Ürün sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="778e0-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="778e0-103">.NET Framework 4,6 ve üzeri sürümlerde, ürün sürümü oluşturma işlemi önceki .NET Framework sürümlerinden (.NET Framework 4, 4,5, 4.5.1 ve 4.5.2) değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="778e0-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="778e0-104">Ürün sürümü oluşturma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="778e0-104">Product versioning changes</span></span>

<span data-ttu-id="778e0-105">Ayrıntılı değişiklikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="778e0-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="778e0-106">`Version` `4.6.` `4.7.` Anahtardaki girdinin değeri, .NET Framework 4,6 ve noktası sürümleri için xxxxx, .NET Framework 4,7 için xxxxx olarak değiştirilmiştir. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`</span><span class="sxs-lookup"><span data-stu-id="778e0-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="778e0-107">.NET Framework 4,5, 4.5.1 ve 4.5.2 ' de, `4.5.` *xxxxx*biçiminde vardı.</span><span class="sxs-lookup"><span data-stu-id="778e0-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="778e0-108">.NET Framework dosyaları için dosya ve ürün sürümü oluşturma, .NET Framework 4,6 ve `4.0.30319.x` `4.7.X.0` noktası sürümleri için ve .NET Framework `4.6.X.0` 4,7 ve noktası sürümleri için için önceki sürüm oluşturma düzeninden değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="778e0-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="778e0-109">Bir dosyaya sağ tıkladıktan sonra dosyanın **özelliklerini** görüntülerken bu yeni değerleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="778e0-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="778e0-110"><xref:System.Version> `4.7.X.0` `4.6.X.0` Yönetilen derlemelerin <xref:System.Reflection.AssemblyInformationalVersionAttribute> ve özniteliklerinin .NET Framework 4,6 ve nokta sürümleri için ve .NET Framework 4,7 için biçimde değerleri vardır. <xref:System.Reflection.AssemblyFileVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="778e0-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="778e0-111">.NET Framework 4,6 ' den başlayarak, <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği sabit sürüm dizesini `4.0.30319.42000`döndürür.</span><span class="sxs-lookup"><span data-stu-id="778e0-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="778e0-112">.NET Framework 4, 4,5, 4.5.1 ve 4.5.2 ' de, sürüm dizelerini 42000 ' den daha düşük `4.0.30319.xxxxx` `xxxxx` olan biçimde döndürür (örneğin, "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="778e0-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="778e0-113"><xref:System.Environment.Version%2A?displayProperty=nameWithType> Özellik üzerinde herhangi bir yeni bağımlılığı alan uygulama kodunu önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="778e0-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="778e0-114">Ürün sürümü oluşturma değişikliklerini işleme</span><span class="sxs-lookup"><span data-stu-id="778e0-114">Handling the product versioning changes</span></span>

<span data-ttu-id="778e0-115">Genel olarak, uygulamalar .NET Framework çalışma zamanı sürümü ve yükleme dizini gibi şeyleri tespit etmek için önerilen tekniklerin üzerine bağımlıdır:</span><span class="sxs-lookup"><span data-stu-id="778e0-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="778e0-116">.NET Framework çalışma zamanı sürümünü algılamak için bkz [. nasıl yapılır: Hangi .NET Framework sürümlerinin yükleneceğini](how-to-determine-which-versions-are-installed.md)saptayın.</span><span class="sxs-lookup"><span data-stu-id="778e0-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="778e0-117">.NET Framework için yükleme yolunu öğrenmek için, `InstallPath` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtardaki girdinin değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="778e0-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="778e0-118">Alt anahtar adı `NET Framework Setup`değil `.NET Framework Setup`,.</span><span class="sxs-lookup"><span data-stu-id="778e0-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="778e0-119">.NET Framework ortak dil çalışma zamanının dizin yolunu öğrenmek için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="778e0-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="778e0-120">CLR sürümünü almak için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="778e0-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="778e0-121">.NET Framework 4 ve nokta sürümleri (.NET Framework 4,5, 4.5.1, 4.5.2 ve .NET Framework 4,6, 4.6.1, 4.6.2 ve 4,7) için, dizeyi `v4.0.30319`döndürür.</span><span class="sxs-lookup"><span data-stu-id="778e0-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="778e0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="778e0-122">See also</span></span>

- [<span data-ttu-id="778e0-123">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="778e0-123">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
