---
title: Metin dosyasından okuma- C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705021"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="0f3fa-102">Bir metin dosyasından okuma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0f3fa-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="0f3fa-103">Bu örnek, <xref:System.IO.File?displayProperty=nameWithType> sınıfından statik yöntemleri <xref:System.IO.File.ReadAllText%2A> ve <xref:System.IO.File.ReadAllLines%2A> kullanarak bir metin dosyasının içeriğini okur.</span><span class="sxs-lookup"><span data-stu-id="0f3fa-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="0f3fa-104"><xref:System.IO.StreamReader>kullanan bir örnek için, bkz. bir [metin dosyasını tek seferde bir satır okuma](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="0f3fa-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0f3fa-105">Bu örnekte kullanılan dosyalar, [bir metin dosyasına nasıl yazılacağı](./how-to-write-to-a-text-file.md)konusunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0f3fa-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="0f3fa-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f3fa-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f3fa-107">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="0f3fa-107">Compiling the Code</span></span>  
 <span data-ttu-id="0f3fa-108">Kodu kopyalayın ve bir C# konsol uygulamasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="0f3fa-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="0f3fa-109">[Bir metin dosyasına yazma](./how-to-write-to-a-text-file.md)işleminden gelen metin dosyalarını kullanmıyorsanız, bağımsız değişkeni `ReadAllText` ve `ReadAllLines` bilgisayarınızdaki uygun yol ve dosya adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0f3fa-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="0f3fa-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0f3fa-110">Robust Programming</span></span>  
 <span data-ttu-id="0f3fa-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0f3fa-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0f3fa-112">Dosya yok veya belirtilen konumda yok.</span><span class="sxs-lookup"><span data-stu-id="0f3fa-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="0f3fa-113">Dosya adının yolunu ve yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0f3fa-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0f3fa-114">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0f3fa-114">.NET Framework Security</span></span>  
 <span data-ttu-id="0f3fa-115">Dosyanın içeriğini belirlemekte bir dosyanın adına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="0f3fa-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="0f3fa-116">Örneğin, `myFile.cs` dosyası bir C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0f3fa-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f3fa-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f3fa-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="0f3fa-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0f3fa-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0f3fa-119">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0f3fa-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
