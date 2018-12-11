---
title: 'Nasıl Yapılır: Dosyalar, klasörler ve sürücüler - hakkında bilgi almak C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: e3b0834f27fd0673687dc00b861e80752a585737
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243965"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="0f593-102">Nasıl Yapılır: Dosyalar, klasörler ve sürücüler hakkında bilgi edinin (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0f593-102">How to: Get Information About Files, Folders, and Drives  (C# Programming Guide)</span></span>
<span data-ttu-id="0f593-103">.NET Framework, dosya sistemi bilgileri aşağıdaki sınıfları kullanarak erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f593-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="0f593-104"><xref:System.IO.FileInfo> Ve <xref:System.IO.DirectoryInfo> sınıfları bir dosya veya dizin temsil eder ve NTFS dosya sistemi tarafından desteklenen dosya özniteliklerin çoğu kullanıma sunan özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="0f593-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="0f593-105">Bunlar ayrıca açma, kapatma, taşıma ve dosya ve klasörleri silme yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0f593-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="0f593-106">Bu sınıfların örnekleri oluşturucuya dosya, klasör veya sürücüde adını temsil eden bir dize geçirerek oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f593-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="0f593-107">Çağrıları kullanarak dosyalara, klasörlere veya sürücüleri adlarını de edinebilirsiniz <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, ve <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0f593-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0f593-108"><xref:System.IO.Directory?displayProperty=nameWithType> Ve <xref:System.IO.File?displayProperty=nameWithType> sınıfları, dizinler ve dosyalar hakkında bilgi almak için statik yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f593-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f593-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f593-109">Example</span></span>  
 <span data-ttu-id="0f593-110">Aşağıdaki örnek, dosyalar ve klasörler hakkındaki bilgilere erişmek için çeşitli yollar gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f593-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0f593-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0f593-111">Robust Programming</span></span>  
 <span data-ttu-id="0f593-112">Kullanıcı tanımlı yol dizelerini işlediğinizde, özel durumlar için aşağıdaki koşullar da işlemesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="0f593-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
-   <span data-ttu-id="0f593-113">Dosya adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="0f593-113">The file name is malformed.</span></span> <span data-ttu-id="0f593-114">Örneğin, geçersiz karakterler veya yalnızca boşluk içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0f593-114">For example, it contains invalid characters or only white space.</span></span>  
  
-   <span data-ttu-id="0f593-115">Dosya adı null.</span><span class="sxs-lookup"><span data-stu-id="0f593-115">The file name is null.</span></span>  
  
-   <span data-ttu-id="0f593-116">Dosya adı sistem tarafından tanımlanan uzunluk üst sınırından daha uzun.</span><span class="sxs-lookup"><span data-stu-id="0f593-116">The file name is longer than the system-defined maximum length.</span></span>  
  
-   <span data-ttu-id="0f593-117">Dosya adı iki nokta üst üste (:) içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0f593-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="0f593-118">Uygulama belirtilen dosyayı okumak için yeterli izinlere sahip değilse `Exists` yöntemi döndürür `false` bağımsız olarak, bir yolu var olup; yöntemi bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="0f593-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f593-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f593-119">See Also</span></span>

- <xref:System.IO?displayProperty=nameWithType>  
- [<span data-ttu-id="0f593-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0f593-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0f593-121">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0f593-121">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
