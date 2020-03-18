---
title: Metin dosyasından okuma - C# Programlama Kılavuzu
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705021"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="4948e-102">Metin dosyasından okuma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4948e-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="4948e-103">Bu örnek, statik yöntemleri <xref:System.IO.File.ReadAllText%2A> kullanarak ve <xref:System.IO.File.ReadAllLines%2A> sınıftan bir <xref:System.IO.File?displayProperty=nameWithType> metin dosyasının içeriğini okur.</span><span class="sxs-lookup"><span data-stu-id="4948e-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="4948e-104">Kullanan bir örnek <xref:System.IO.StreamReader>için, [metin dosyasını bir defada bir satırda nasıl okunabildiğini](./how-to-read-a-text-file-one-line-at-a-time.md)görün.</span><span class="sxs-lookup"><span data-stu-id="4948e-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="4948e-105">Bu örnekte kullanılan dosyalar bir metin [dosyasına nasıl yazılır](./how-to-write-to-a-text-file.md)konusunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4948e-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="4948e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4948e-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4948e-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4948e-107">Compiling the Code</span></span>  
 <span data-ttu-id="4948e-108">Kodu kopyalayın ve C# konsol uygulamasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="4948e-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="4948e-109">Metin dosyalarını [metin dosyasına yazma hakkında niçin](./how-to-write-to-a-text-file.md)kullanmıyorsanız, `ReadAllText` bağımsız `ReadAllLines` değişkeni bilgisayarınızdaki uygun yol ve dosya adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4948e-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="4948e-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="4948e-110">Robust Programming</span></span>  
 <span data-ttu-id="4948e-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="4948e-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4948e-112">Dosya belirtilen konumda yok veya yok.</span><span class="sxs-lookup"><span data-stu-id="4948e-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="4948e-113">Dosya adının yolunu ve yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4948e-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4948e-114">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4948e-114">.NET Framework Security</span></span>  
 <span data-ttu-id="4948e-115">Dosyanın içeriğini belirlemek için bir dosyanın adına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="4948e-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="4948e-116">Örneğin, dosya `myFile.cs` C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4948e-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4948e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4948e-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="4948e-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4948e-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4948e-119">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4948e-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
