---
title: '#pragma sağlama - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 36e5602f0a0b872a4aa6cdac64b49b1d1c708795
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877521"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="41451-102">#pragma sağlama toplamı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="41451-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="41451-103">ASP.NET sayfaları hatalarını ayıklamaya yardımcı olmak kaynak dosyalar için sağlama toplamları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41451-103">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41451-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41451-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="41451-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41451-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="41451-106">İzleme gerektiren değişiklikleri veya güncelleştirmeleri için dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="41451-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="41451-107">Genel benzersiz tanıtıcısı (GUID) karma algoritması için.</span><span class="sxs-lookup"><span data-stu-id="41451-107">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="41451-108">Sağlama toplamı baytını temsil eden bir onaltılık basamak dizisi.</span><span class="sxs-lookup"><span data-stu-id="41451-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="41451-109">Onaltı basamaklı bir çift sayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41451-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="41451-110">Bir derleme zamanı uyarı ve yönerge basamak sonuçları tek sayıda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="41451-110">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41451-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41451-111">Remarks</span></span>  
 <span data-ttu-id="41451-112">Visual Studio hata ayıklayıcı her zaman doğru kaynak bulduğu emin olmak için bir sağlama toplamı kullanır.</span><span class="sxs-lookup"><span data-stu-id="41451-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="41451-113">Derleyici, bir kaynak dosyası için sağlama toplamını hesaplar ve ardından program veritabanı (PDB) dosyası çıktıyı yayar.</span><span class="sxs-lookup"><span data-stu-id="41451-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="41451-114">Hata ayıklayıcı, PDB sonra kaynak dosyasını hesaplar sağlama toplamı karşılaştırma için kullanır.</span><span class="sxs-lookup"><span data-stu-id="41451-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="41451-115">Bu çözüm, .aspx dosyası yerine üretilen kaynak dosyası için hesaplanan sağlama toplamı olduğu için ASP.NET projeleri için çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="41451-115">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="41451-116">Bu sorunu gidermek için `#pragma checksum` ASP.NET sayfaları için sağlama toplamı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="41451-116">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="41451-117">Görselde bir ASP.NET projesi oluşturduğunuzda, C#, üretilen kaynak dosyası içinden kaynak oluşturulduğunda .aspx dosyası, bir sağlama toplamı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="41451-117">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="41451-118">Derleyici, daha sonra bu bilgileri PDB dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="41451-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="41451-119">Derleyici Hayır karşılaşırsa `#pragma checksum` dosyasındaki yönergesi, sağlama toplamını hesaplar ve değeri PDB dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="41451-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41451-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="41451-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="41451-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41451-121">See also</span></span>

- [<span data-ttu-id="41451-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="41451-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="41451-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="41451-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="41451-124">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="41451-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
