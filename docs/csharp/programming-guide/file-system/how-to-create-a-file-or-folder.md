---
title: Bir dosya veya klasör oluşturma-C# Programlama Kılavuzu
description: Program aracılığıyla bir dosya veya klasör oluşturmayı öğrenin. Bir klasör, alt klasör, alt klasörde bir dosya oluşturabilir ve bu dosyaya veri yazabilirsiniz.
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: f5641dc765b1a2d62adb76babe3f111730d4550b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302691"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="42879-104">Dosya veya klasör oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="42879-104">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="42879-105">Bilgisayarınızda program aracılığıyla bir klasör oluşturabilir, bir alt klasör oluşturabilir, alt klasörde bir dosya oluşturabilir ve verileri dosyaya yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42879-105">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42879-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="42879-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="42879-107">Klasör zaten varsa, <xref:System.IO.Directory.CreateDirectory%2A> hiçbir şey yapmaz ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="42879-107">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="42879-108">Ancak, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> varolan bir dosyayı yeni bir dosya ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="42879-108">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="42879-109">Örnek, varolan bir `if` - `else` dosyanın değiştirilmesini engellemek için bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="42879-109">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="42879-110">Örnekte aşağıdaki değişiklikleri yaparak, belirli bir ada sahip bir dosyanın zaten mevcut olup olmadığına bağlı olarak farklı sonuçlar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42879-110">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="42879-111">Böyle bir dosya yoksa, kod bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42879-111">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="42879-112">Böyle bir dosya varsa, kod bu dosyaya veri ekler.</span><span class="sxs-lookup"><span data-stu-id="42879-112">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="42879-113">Rastgele olmayan bir dosya adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="42879-113">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="42879-114">`if` - `else` İfadesini `using` aşağıdaki koddaki ifadesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="42879-114">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="42879-115">Her seferinde verilerin dosyaya eklendiğini doğrulamak için örneği birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="42879-115">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="42879-116">Deneyebileceğiniz daha fazla `FileMode` değer için bkz <xref:System.IO.FileMode> ..</span><span class="sxs-lookup"><span data-stu-id="42879-116">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="42879-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="42879-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="42879-118">Klasör adı hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="42879-118">The folder name is malformed.</span></span> <span data-ttu-id="42879-119">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk ( <xref:System.ArgumentException> sınıf) içeriyor.</span><span class="sxs-lookup"><span data-stu-id="42879-119">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="42879-120"><xref:System.IO.Path>Geçerli yol adları oluşturmak için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="42879-120">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="42879-121">Oluşturulacak klasörün üst klasörü salt okunurdur ( <xref:System.IO.IOException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="42879-121">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="42879-122">Klasör adı `null` ( <xref:System.ArgumentNullException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="42879-122">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="42879-123">Klasör adı çok uzun ( <xref:System.IO.PathTooLongException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="42879-123">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="42879-124">Klasör adı yalnızca bir iki nokta üst üste, ":" ( <xref:System.IO.PathTooLongException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="42879-124">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="42879-125">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="42879-125">.NET Security</span></span>  
 <span data-ttu-id="42879-126"><xref:System.Security.SecurityException>Kısmi güven durumlarında sınıfın bir örneği oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="42879-126">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="42879-127">Klasörü oluşturma izniniz yoksa, örnek sınıfının bir örneğini oluşturur <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="42879-127">If you don't have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42879-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42879-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="42879-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="42879-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="42879-130">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="42879-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
