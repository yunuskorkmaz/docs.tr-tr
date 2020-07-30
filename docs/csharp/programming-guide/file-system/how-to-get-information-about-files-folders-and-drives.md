---
title: Dosyalar, klasörler ve sürücüler hakkında bilgi edinme-C# Programlama Kılavuzu
description: Dosyalar, klasörler ve sürücüler hakkında bilgi alma hakkında bilgi edinin. Bir kod örneğine ve kullanılabilir ek kaynaklara bakın.
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: f696cd90f197bede1a64949d211a563ce9a18376
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299935"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="067e8-104">Dosyalar, klasörler ve sürücüler hakkında bilgi alma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="067e8-104">How to get information about files, folders, and drives  (C# Programming Guide)</span></span>
<span data-ttu-id="067e8-105">.NET ' te aşağıdaki sınıfları kullanarak dosya sistemi bilgilerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="067e8-105">In .NET, you can access file system information by using the following classes:</span></span>  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="067e8-106"><xref:System.IO.FileInfo>Ve <xref:System.IO.DirectoryInfo> sınıfları bir dosya veya dizini temsil eder ve NTFS dosya sistemi tarafından desteklenen dosya özniteliklerinin çoğunu açığa çıkaran özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="067e8-106">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="067e8-107">Ayrıca dosya ve klasörleri açma, kapatma, taşıma ve silme yöntemleri de bulunur.</span><span class="sxs-lookup"><span data-stu-id="067e8-107">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="067e8-108">Oluşturucuya dosya, klasör veya sürücü adını temsil eden bir dize geçirerek, bu sınıfların örneklerini oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="067e8-108">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="067e8-109">Ayrıca, ve için yapılan çağrıları kullanarak dosyaların, klasörlerin veya sürücülerin adlarını elde edebilirsiniz <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="067e8-109">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="067e8-110"><xref:System.IO.Directory?displayProperty=nameWithType>Ve <xref:System.IO.File?displayProperty=nameWithType> sınıfları, dizinler ve dosyalar hakkında bilgi almak için statik yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="067e8-110">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="067e8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="067e8-111">Example</span></span>  
 <span data-ttu-id="067e8-112">Aşağıdaki örnek dosya ve klasörlerle ilgili bilgilere erişmek için çeşitli yollar gösterir.</span><span class="sxs-lookup"><span data-stu-id="067e8-112">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="067e8-113">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="067e8-113">Robust Programming</span></span>  
 <span data-ttu-id="067e8-114">Kullanıcı tarafından belirtilen yol dizelerini işlerken aşağıdaki koşullarda özel durumları da işlemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="067e8-114">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
- <span data-ttu-id="067e8-115">Dosya adı hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="067e8-115">The file name is malformed.</span></span> <span data-ttu-id="067e8-116">Örneğin, geçersiz karakterler veya yalnızca boşluk içeriyor.</span><span class="sxs-lookup"><span data-stu-id="067e8-116">For example, it contains invalid characters or only white space.</span></span>  
  
- <span data-ttu-id="067e8-117">Dosya adı null.</span><span class="sxs-lookup"><span data-stu-id="067e8-117">The file name is null.</span></span>  
  
- <span data-ttu-id="067e8-118">Dosya adı sistem tarafından tanımlanan uzunluk üst sınırından daha uzun.</span><span class="sxs-lookup"><span data-stu-id="067e8-118">The file name is longer than the system-defined maximum length.</span></span>  
  
- <span data-ttu-id="067e8-119">Dosya adı iki nokta üst üste (:)) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="067e8-119">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="067e8-120">Uygulama, belirtilen dosyayı okumak için yeterli izinlere sahip değilse, `Exists` Yöntem `false` bir yolun var olup olmadığına bakılmaksızın döndürülür; Yöntem bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="067e8-120">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067e8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="067e8-121">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="067e8-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="067e8-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="067e8-123">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="067e8-123">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
