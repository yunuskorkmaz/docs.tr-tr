---
title: Dosya veya klasör oluşturma- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: e0d0a7fbbc7e6a5c9a0bd00dec1188c5cfdcf896
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705255"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="8f199-102">Dosya veya klasör oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8f199-102">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="8f199-103">Bilgisayarınızda program aracılığıyla bir klasör oluşturabilir, bir alt klasör oluşturabilir, alt klasörde bir dosya oluşturabilir ve verileri dosyaya yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f199-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f199-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f199-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="8f199-105">Klasör zaten varsa, <xref:System.IO.Directory.CreateDirectory%2A> hiçbir şey yapmaz ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="8f199-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="8f199-106">Ancak, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> var olan bir dosyayı yeni bir dosya ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8f199-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="8f199-107">Örnek, varolan bir dosyanın değiştirilmesini engellemek için bir `if`-`else` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f199-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="8f199-108">Örnekte aşağıdaki değişiklikleri yaparak, belirli bir ada sahip bir dosyanın zaten mevcut olup olmadığına bağlı olarak farklı sonuçlar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f199-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="8f199-109">Böyle bir dosya yoksa, kod bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f199-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="8f199-110">Böyle bir dosya varsa, kod bu dosyaya veri ekler.</span><span class="sxs-lookup"><span data-stu-id="8f199-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="8f199-111">Rastgele olmayan bir dosya adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="8f199-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="8f199-112">`if`-`else` ifadesini aşağıdaki koddaki `using` ifadesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8f199-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="8f199-113">Her seferinde verilerin dosyaya eklendiğini doğrulamak için örneği birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8f199-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="8f199-114">Deneyebileceğiniz daha fazla `FileMode` değer için bkz. <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="8f199-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="8f199-115">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="8f199-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8f199-116">Klasör adı hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="8f199-116">The folder name is malformed.</span></span> <span data-ttu-id="8f199-117">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="8f199-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="8f199-118">Geçerli yol adları oluşturmak için <xref:System.IO.Path> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8f199-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="8f199-119">Oluşturulacak klasörün üst klasörü salt okunurdur (<xref:System.IO.IOException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="8f199-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="8f199-120">Klasör adı `null` (<xref:System.ArgumentNullException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="8f199-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="8f199-121">Klasör adı çok uzun (<xref:System.IO.PathTooLongException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="8f199-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="8f199-122">Klasör adı yalnızca bir iki nokta üst üste, ":" (<xref:System.IO.PathTooLongException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="8f199-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8f199-123">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8f199-123">.NET Framework Security</span></span>  
 <span data-ttu-id="8f199-124">Kısmi güven durumlarında <xref:System.Security.SecurityException> sınıfının bir örneği oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="8f199-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="8f199-125">Klasörü oluşturma izniniz yoksa, örnek <xref:System.UnauthorizedAccessException> sınıfının bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f199-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f199-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f199-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="8f199-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8f199-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8f199-128">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8f199-128">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
