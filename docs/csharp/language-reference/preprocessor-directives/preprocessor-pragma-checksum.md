---
title: '#pragma sağlama toplamı C# -başvuru'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 4103b6262fc5085c1204f423a36c9c5c2053b497
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605656"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="7ee1f-102">#pragma sağlama toplamı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7ee1f-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="7ee1f-103">ASP.NET sayfalarında hata ayıklamaya yardımcı olmak için kaynak dosyaları için sağlama toplamı üretir.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-103">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ee1f-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ee1f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ee1f-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="7ee1f-106">Değişiklik veya güncelleştirme için izlemeyi gerektiren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="7ee1f-107">Karma algoritma için genel benzersiz tanımlayıcı (GUID).</span><span class="sxs-lookup"><span data-stu-id="7ee1f-107">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="7ee1f-108">Sağlama toplamı baytlarını temsil eden onaltılık basamakların dizesi.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="7ee1f-109">Çift sayıda onaltılık basamak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="7ee1f-110">Tek sayıda basamak derleme zamanı uyarısına neden olur ve yönerge yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-110">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ee1f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ee1f-111">Remarks</span></span>  
 <span data-ttu-id="7ee1f-112">Visual Studio hata ayıklayıcı, her zaman doğru kaynağı bulmasını sağlamak için bir sağlama toplamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="7ee1f-113">Derleyici, kaynak dosya için sağlama toplamını hesaplar ve sonra çıktıyı program veritabanı (PDB) dosyasına yayar.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="7ee1f-114">Hata ayıklayıcı daha sonra kaynak dosya için hesapladığı sağlama toplamıyla karşılaştırmak için PDB 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="7ee1f-115">Hesaplanan sağlama toplamı,. aspx dosyası yerine oluşturulan kaynak dosya için olduğundan, bu çözüm ASP.NET projelerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-115">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="7ee1f-116">Bu sorunu `#pragma checksum` gidermek için ASP.NET sayfaları için sağlama toplamı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-116">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="7ee1f-117">Görselde C#bir ASP.NET projesi oluşturduğunuzda oluşturulan kaynak dosya, kaynağın oluşturulduğu. aspx dosyası için bir sağlama toplamı içerir.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-117">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="7ee1f-118">Derleyici daha sonra bu bilgileri PDB dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="7ee1f-119">Derleyici dosyada hiçbir `#pragma checksum` yönergeyle karşılaşırsa, sağlama toplamını hesaplar ve değeri pdb dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ee1f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ee1f-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ee1f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-121">See also</span></span>

- [<span data-ttu-id="7ee1f-122">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="7ee1f-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7ee1f-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7ee1f-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7ee1f-124">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="7ee1f-124">C# Preprocessor Directives</span></span>](./index.md)
