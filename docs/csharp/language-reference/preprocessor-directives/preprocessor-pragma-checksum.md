---
title: '#pragma checksum - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 1bbb404e1183daa5e68e512e7439b6ae52abd605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712487"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="4cdd6-102">#pragma sağlama toplamı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4cdd6-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="4cdd6-103">Hata ayıklama ASP.NET sayfalarına yardımcı olmak için kaynak dosyaları için denetimler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-103">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cdd6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cdd6-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cdd6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cdd6-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="4cdd6-106">Değişiklikler veya güncelleştirmeler için izleme gerektiren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="4cdd6-107">Karma algoritmaiçin Genel Olarak Benzersiz Tanımlayıcı (GUID).</span><span class="sxs-lookup"><span data-stu-id="4cdd6-107">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="4cdd6-108">Çeklerin baytlarını temsil eden hexadecimal basamaklar dizesi.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="4cdd6-109">Hexadecimal basamakların çift sayısı olmalı.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="4cdd6-110">Tek sayıda basamak, derleme zamanı uyarısı ile sonuçlanır ve yönerge yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-110">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cdd6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cdd6-111">Remarks</span></span>  
 <span data-ttu-id="4cdd6-112">Visual Studio hata ayıklama her zaman doğru kaynağı bulduğundan emin olmak için bir checksum kullanır.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="4cdd6-113">Derleyici bir kaynak dosya için denetim umunu hesaplar ve çıktıyı program veritabanı (PDB) dosyasına yalar.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="4cdd6-114">Hata ayıklama, kaynak dosyayı hesapladığını denetler karşıkarşılaştırmak için PDB'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="4cdd6-115">Bu çözüm, ASP.NET projelerde çalışmaz, çünkü hesaplanmış denetimler .aspx dosyası yerine oluşturulan kaynak dosya içindir.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-115">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="4cdd6-116">Bu sorunu gidermek `#pragma checksum` için, ASP.NET sayfaları için checksum desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-116">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="4cdd6-117">Visual C#'da bir ASP.NET projesi oluşturduğunuzda, oluşturulan kaynak dosyası,.kaynak dosyanın oluşturulduğu .aspx dosyası için bir denetim umumu içerir.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-117">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="4cdd6-118">Derleyici daha sonra bu bilgileri PDB dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="4cdd6-119">Derleyici dosyada yönergeyle `#pragma checksum` karşılaşmazsa, denetimleri hesaplar ve değeri PDB dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cdd6-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="4cdd6-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cdd6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-121">See also</span></span>

- [<span data-ttu-id="4cdd6-122">C# Referans</span><span class="sxs-lookup"><span data-stu-id="4cdd6-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4cdd6-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4cdd6-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4cdd6-124">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="4cdd6-124">C# Preprocessor Directives</span></span>](./index.md)
