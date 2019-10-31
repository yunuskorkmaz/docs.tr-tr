---
title: 'Azaltma: Ürün Sürümü Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 63075136b7de4aeaa4f94c092996ae1829b449a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126165"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="0f1a7-102">Azaltma: Ürün Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0f1a7-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="0f1a7-103">.NET Framework 4,6 ve üzeri sürümlerde, ürün sürümü oluşturma işlemi önceki .NET Framework sürümlerinden (.NET Framework 4, 4,5, 4.5.1 ve 4.5.2) değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="0f1a7-104">Ürün sürümü oluşturma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="0f1a7-104">Product versioning changes</span></span>

<span data-ttu-id="0f1a7-105">Ayrıntılı değişiklikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="0f1a7-106">`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtarındaki `Version` girdinin değeri .NET Framework 4,6 ve noktası sürümleri için `4.6.`*xxxxx* , `4.7.`4,7 için .NET Framework *xxxxx* olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="0f1a7-107">.NET Framework 4,5, 4.5.1 ve 4.5.2 `4.5.`*xxxxx*biçiminde vardı.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="0f1a7-108">.NET Framework dosyaları için dosya ve ürün sürümü oluşturma, .NET Framework 4,6 ve noktası sürümleri için `4.6.X.0` `4.0.30319.x` önceki sürüm oluşturma düzeninden değiştirilmiştir ve `4.7.X.0` 4,7 ve noktası sürümleri için .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="0f1a7-109">Bir dosyaya sağ tıkladıktan sonra dosyanın **özelliklerini** görüntülerken bu yeni değerleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="0f1a7-110">Yönetilen derlemeler için <xref:System.Reflection.AssemblyFileVersionAttribute> ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> öznitelikleri, .NET Framework 4,6 ve noktası sürümleri için `4.6.X.0` ve `4.7.X.0` 4,7 .NET Framework için formda <xref:System.Version> değerlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="0f1a7-111">.NET Framework 4,6 ' den itibaren <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği, `4.0.30319.42000`sabit sürüm dizesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="0f1a7-112">.NET Framework 4, 4,5, 4.5.1 ve 4.5.2 ' de, sürüm dizelerini `xxxxx` 42000 ' den küçük olan `4.0.30319.xxxxx` biçiminde döndürür (örneğin, "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="0f1a7-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="0f1a7-113">Uygulama kodunun <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği üzerinde herhangi bir yeni bağımlılığı alan önermediğine göz önünde bulunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="0f1a7-114">Ürün sürümü oluşturma değişikliklerini işleme</span><span class="sxs-lookup"><span data-stu-id="0f1a7-114">Handling the product versioning changes</span></span>

<span data-ttu-id="0f1a7-115">Genel olarak, uygulamalar .NET Framework çalışma zamanı sürümü ve yükleme dizini gibi şeyleri tespit etmek için önerilen tekniklerin üzerine bağımlıdır:</span><span class="sxs-lookup"><span data-stu-id="0f1a7-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="0f1a7-116">.NET Framework çalışma zamanı sürümünü algılamak için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="0f1a7-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="0f1a7-117">.NET Framework yükleme yolunu öğrenmek için `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtarındaki `InstallPath` girişinin değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="0f1a7-118">Alt anahtar adı, `.NET Framework Setup`değil `NET Framework Setup`.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="0f1a7-119">.NET Framework ortak dil çalışma zamanının dizin yolunu öğrenmek için, <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="0f1a7-120">CLR sürümünü almak için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="0f1a7-121">.NET Framework 4 ve nokta sürümleri (.NET Framework 4,5, 4.5.1, 4.5.2 ve .NET Framework 4,6, 4.6.1, 4.6.2 ve 4,7) için, `v4.0.30319`dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f1a7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f1a7-122">See also</span></span>

- [<span data-ttu-id="0f1a7-123">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="0f1a7-123">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
