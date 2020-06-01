---
title: Bir metin dosyasından okuma-C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 8f79d22a86390ca931b05262e50865d852c154c7
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241753"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="f91ec-102">Bir metin dosyasından okuma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f91ec-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="f91ec-103">Bu örnek, statik yöntemleri ve sınıfından kullanarak bir metin dosyasının içeriğini okur <xref:System.IO.File.ReadAllText%2A> <xref:System.IO.File.ReadAllLines%2A> <xref:System.IO.File?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f91ec-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="f91ec-104">Kullanan bir örnek için <xref:System.IO.StreamReader> , bkz. [bir metin dosyasını tek seferde bir satır okuma](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="f91ec-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f91ec-105">Bu örnekte kullanılan dosyalar, [bir metin dosyasına nasıl yazılacağı](./how-to-write-to-a-text-file.md)konusunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f91ec-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="f91ec-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f91ec-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f91ec-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f91ec-107">Compiling the Code</span></span>  
 <span data-ttu-id="f91ec-108">Kodu kopyalayın ve bir C# konsol uygulamasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="f91ec-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="f91ec-109">[Bir metin dosyasına yazma](./how-to-write-to-a-text-file.md)işleminden gelen metin dosyalarını kullanmıyorsanız, bağımsız değişkenini `ReadAllText` `ReadAllLines` bilgisayarınızdaki uygun yol ve dosya adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f91ec-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="f91ec-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f91ec-110">Robust Programming</span></span>  
 <span data-ttu-id="f91ec-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="f91ec-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f91ec-112">Dosya yok veya belirtilen konumda yok.</span><span class="sxs-lookup"><span data-stu-id="f91ec-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="f91ec-113">Dosya adının yolunu ve yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f91ec-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="f91ec-114">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="f91ec-114">.NET Security</span></span>  
 <span data-ttu-id="f91ec-115">Dosyanın içeriğini belirlemekte bir dosyanın adına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="f91ec-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="f91ec-116">Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f91ec-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91ec-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f91ec-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="f91ec-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f91ec-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f91ec-119">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f91ec-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
