---
title: Dosya veya klasör oluşturma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: cdcc0a375aa1eca29c024d1e0c9008f337d0c772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167563"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="0bfa2-102">Dosya veya klasör oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0bfa2-102">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="0bfa2-103">Bilgisayarınızda programlı bir klasör oluşturabilir, bir alt klasör oluşturabilir, alt klasörde bir dosya oluşturabilir ve dosyaya veri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bfa2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bfa2-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="0bfa2-105">Klasör zaten varsa, <xref:System.IO.Directory.CreateDirectory%2A> hiçbir şey yapmaz ve hiçbir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="0bfa2-106">Ancak, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> varolan bir dosyayı yeni bir dosyayla değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="0bfa2-107">Örnek, varolan bir dosyanın değiştirilmesini önlemek için bir `if` - `else` deyim kullanır.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="0bfa2-108">Örnekte aşağıdaki değişiklikleri yaparak, belirli bir ada sahip bir dosyanın zaten var olup olmadığına bağlı olarak farklı sonuçlar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="0bfa2-109">Böyle bir dosya yoksa, kod bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="0bfa2-110">Böyle bir dosya varsa, kod verileri o dosyaya ekler.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="0bfa2-111">Rasgele olmayan bir dosya adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="0bfa2-112">İfadeyi `if` - `else` aşağıdaki `using` koddaki deyimle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="0bfa2-113">Verilerin her seferinde dosyaya eklenmesini doğrulamak için örneği birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="0bfa2-114">Deneyebileceğiniz `FileMode` daha fazla değer <xref:System.IO.FileMode>için bkz.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="0bfa2-115">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0bfa2-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0bfa2-116">Klasör adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-116">The folder name is malformed.</span></span> <span data-ttu-id="0bfa2-117">Örneğin, yasadışı karakterler içerir veya yalnızca beyaz<xref:System.ArgumentException> boşluk (sınıf) olduğunu.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="0bfa2-118">Geçerli <xref:System.IO.Path> yol adları oluşturmak için sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="0bfa2-119">Oluşturulacak klasörün üst klasörü salt okunur<xref:System.IO.IOException> (sınıf) olur.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="0bfa2-120">Klasör adı `null` (sınıf).<xref:System.ArgumentNullException></span><span class="sxs-lookup"><span data-stu-id="0bfa2-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="0bfa2-121">Klasör adı çok uzun<xref:System.IO.PathTooLongException> (sınıf).</span><span class="sxs-lookup"><span data-stu-id="0bfa2-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="0bfa2-122">Klasör adı sadece bir iki<xref:System.IO.PathTooLongException> nokta üst üste, ":" (sınıf).</span><span class="sxs-lookup"><span data-stu-id="0bfa2-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0bfa2-123">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0bfa2-123">.NET Framework Security</span></span>  
 <span data-ttu-id="0bfa2-124"><xref:System.Security.SecurityException> Sınıfın bir örneği kısmi güven durumlarında atılabilir.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="0bfa2-125">Klasörü oluşturma izniniz yoksa, örnek sınıfın bir örneğini <xref:System.UnauthorizedAccessException> atar.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bfa2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bfa2-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="0bfa2-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0bfa2-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0bfa2-128">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0bfa2-128">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
