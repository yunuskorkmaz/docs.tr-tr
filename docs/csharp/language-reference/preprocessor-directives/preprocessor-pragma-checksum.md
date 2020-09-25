---
description: '#pragma sağlama toplamı-C# başvurusu'
title: '#pragma sağlama toplamı-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: df665704ac813adbbf6473e81fad0a1c7ff616d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168575"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="83bbd-103">#pragma sağlama toplamı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="83bbd-103">#pragma checksum (C# Reference)</span></span>

<span data-ttu-id="83bbd-104">ASP.NET sayfalarında hata ayıklamaya yardımcı olmak için kaynak dosyaları için sağlama toplamı üretir.</span><span class="sxs-lookup"><span data-stu-id="83bbd-104">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83bbd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83bbd-105">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="83bbd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83bbd-106">Parameters</span></span>  

 `"filename"`  
 <span data-ttu-id="83bbd-107">Değişiklik veya güncelleştirme için izlemeyi gerektiren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="83bbd-107">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="83bbd-108">Karma algoritma için genel benzersiz tanımlayıcı (GUID).</span><span class="sxs-lookup"><span data-stu-id="83bbd-108">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="83bbd-109">Sağlama toplamı baytlarını temsil eden onaltılık basamakların dizesi.</span><span class="sxs-lookup"><span data-stu-id="83bbd-109">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="83bbd-110">Çift sayıda onaltılık basamak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83bbd-110">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="83bbd-111">Tek sayıda basamak derleme zamanı uyarısına neden olur ve yönerge yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="83bbd-111">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83bbd-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83bbd-112">Remarks</span></span>  

 <span data-ttu-id="83bbd-113">Visual Studio hata ayıklayıcı, her zaman doğru kaynağı bulmasını sağlamak için bir sağlama toplamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="83bbd-113">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="83bbd-114">Derleyici, kaynak dosya için sağlama toplamını hesaplar ve sonra çıktıyı program veritabanı (PDB) dosyasına yayar.</span><span class="sxs-lookup"><span data-stu-id="83bbd-114">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="83bbd-115">Hata ayıklayıcı daha sonra kaynak dosya için hesapladığı sağlama toplamıyla karşılaştırmak için PDB 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="83bbd-115">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="83bbd-116">Hesaplanan sağlama toplamı,. aspx dosyası yerine oluşturulan kaynak dosya için olduğundan, bu çözüm ASP.NET projelerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="83bbd-116">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="83bbd-117">Bu sorunu gidermek için `#pragma checksum` ASP.NET sayfaları için sağlama toplamı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="83bbd-117">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="83bbd-118">Visual C# içinde bir ASP.NET projesi oluşturduğunuzda oluşturulan kaynak dosya, kaynağın oluşturulduğu. aspx dosyası için bir sağlama toplamı içerir.</span><span class="sxs-lookup"><span data-stu-id="83bbd-118">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="83bbd-119">Derleyici daha sonra bu bilgileri PDB dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="83bbd-119">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="83bbd-120">Derleyici `#pragma checksum` dosyada hiçbir yönergeyle karşılaşırsa, sağlama toplamını hesaplar ve DEĞERI pdb dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="83bbd-120">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83bbd-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="83bbd-121">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="83bbd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83bbd-122">See also</span></span>

- [<span data-ttu-id="83bbd-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="83bbd-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="83bbd-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="83bbd-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="83bbd-125">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="83bbd-125">C# Preprocessor Directives</span></span>](./index.md)
