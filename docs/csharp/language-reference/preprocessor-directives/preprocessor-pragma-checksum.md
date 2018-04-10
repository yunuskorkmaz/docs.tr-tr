---
title: '#pragma sağlama toplamı (C# Başvurusu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0604a559be25c300fcdc6041975306b465fc595f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="34284-102">#pragma sağlama toplamı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="34284-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="34284-103">Hata ayıklamaya yardımcı olmak kaynak dosyaları için sağlama oluşturur [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] sayfaları.</span><span class="sxs-lookup"><span data-stu-id="34284-103">Generates checksums for source files to aid with debugging [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34284-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34284-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34284-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34284-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="34284-106">İzleme gerektiren değişiklikler veya güncelleştirmeler için dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="34284-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="34284-107">Genel benzersiz tanımlayıcı (GUID) dosyası için.</span><span class="sxs-lookup"><span data-stu-id="34284-107">The Globally Unique Identifier (GUID) for the file.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="34284-108">Onaltılık basamak sağlama toplamı baytını temsil eden dize.</span><span class="sxs-lookup"><span data-stu-id="34284-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="34284-109">Onaltılık basamak sayısı bir çift sayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34284-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="34284-110">Derleme zamanı uyarı ve yönergesi basamak sonuçlarında tek sayıda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="34284-110">An odd number of digits results in a compile-time warning, and the directive are  ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34284-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34284-111">Remarks</span></span>  
 <span data-ttu-id="34284-112">Visual Studio hata ayıklayıcısı bir sağlama toplamı her zaman doğru kaynak bulduğu emin olmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="34284-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="34284-113">Derleyici bir kaynak dosya için sağlama toplamı hesaplar ve ardından program veritabanı (PDB) dosyası çıktıyı yayar.</span><span class="sxs-lookup"><span data-stu-id="34284-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="34284-114">Hata ayıklayıcı PDB için kaynak dosyası hesaplar sağlama toplamı Karşılaştırılacak sonra kullanır.</span><span class="sxs-lookup"><span data-stu-id="34284-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="34284-115">Bu çözüm için çalışmaz [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projeleri hesaplanan sağlama toplamı .aspx dosyası yerine oluşturulan kaynak dosya için olduğundan.</span><span class="sxs-lookup"><span data-stu-id="34284-115">This solution does not work for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="34284-116">Bu sorunu gidermek için `#pragma checksum` sağlama toplamı desteği sağlar [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] sayfaları.</span><span class="sxs-lookup"><span data-stu-id="34284-116">To address this problem, `#pragma checksum` provides checksum support for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
 <span data-ttu-id="34284-117">Oluştururken bir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] proje [!INCLUDE[csprcs](~/includes/csprcs-md.md)], sağlama toplamı, kaynak oluşturulduğunda .aspx dosyası için oluşturulan kaynak dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="34284-117">When you create an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] project in [!INCLUDE[csprcs](~/includes/csprcs-md.md)], the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="34284-118">Derleyici, sonra bu bilgileri PDB dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="34284-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="34284-119">Derleyici Hayır karşılaşırsa `#pragma checksum` yönerge dosyasında sağlama toplamı hesaplar ve değeri PDB dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="34284-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34284-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="34284-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="34284-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34284-121">See Also</span></span>  
 [<span data-ttu-id="34284-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="34284-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="34284-123">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="34284-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="34284-124">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="34284-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
