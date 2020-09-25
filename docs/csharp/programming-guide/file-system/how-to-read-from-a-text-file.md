---
title: Bir metin dosyasından okuma-C# Programlama Kılavuzu
description: Dosya sınıfından statik yöntemler kullanarak bir metin dosyasından okumayı öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 64ac99ec0a72ba7df120f6732edccf160a351738
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201843"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="0e1ff-104">Bir metin dosyasından okuma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0e1ff-104">How to read from a text file (C# Programming Guide)</span></span>

<span data-ttu-id="0e1ff-105">Bu örnek, statik yöntemleri ve sınıfından kullanarak bir metin dosyasının içeriğini okur <xref:System.IO.File.ReadAllText%2A> <xref:System.IO.File.ReadAllLines%2A> <xref:System.IO.File?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e1ff-105">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="0e1ff-106">Kullanan bir örnek için <xref:System.IO.StreamReader> , bkz. [bir metin dosyasını tek seferde bir satır okuma](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="0e1ff-106">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0e1ff-107">Bu örnekte kullanılan dosyalar, [bir metin dosyasına nasıl yazılacağı](./how-to-write-to-a-text-file.md)konusunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-107">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="0e1ff-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e1ff-108">Example</span></span>  

 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e1ff-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0e1ff-109">Compiling the Code</span></span>  

 <span data-ttu-id="0e1ff-110">Kodu kopyalayın ve bir C# konsol uygulamasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-110">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="0e1ff-111">[Bir metin dosyasına yazma](./how-to-write-to-a-text-file.md)işleminden gelen metin dosyalarını kullanmıyorsanız, bağımsız değişkenini `ReadAllText` `ReadAllLines` bilgisayarınızdaki uygun yol ve dosya adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-111">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="0e1ff-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0e1ff-112">Robust Programming</span></span>  

 <span data-ttu-id="0e1ff-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0e1ff-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0e1ff-114">Dosya yok veya belirtilen konumda yok.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-114">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="0e1ff-115">Dosya adının yolunu ve yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-115">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="0e1ff-116">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="0e1ff-116">.NET Security</span></span>  

 <span data-ttu-id="0e1ff-117">Dosyanın içeriğini belirlemekte bir dosyanın adına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-117">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="0e1ff-118">Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-118">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e1ff-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e1ff-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="0e1ff-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0e1ff-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0e1ff-121">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0e1ff-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
