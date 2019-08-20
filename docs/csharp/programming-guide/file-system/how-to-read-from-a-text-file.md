---
title: 'Nasıl yapılır: Metin dosyasından okuma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: c424f7884dd7242152bda1b16943f6489194299f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589990"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="e42f7-102">Nasıl yapılır: Metin dosyasından okuma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e42f7-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="e42f7-103">Bu örnek, statik yöntemleri <xref:System.IO.File.ReadAllText%2A> ve <xref:System.IO.File.ReadAllLines%2A> <xref:System.IO.File?displayProperty=nameWithType> sınıfından kullanarak bir metin dosyasının içeriğini okur.</span><span class="sxs-lookup"><span data-stu-id="e42f7-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="e42f7-104">Tarafından kullanılan <xref:System.IO.StreamReader>bir örnek için bkz [. nasıl yapılır: Bir metin dosyasını tek seferde bir satır okur](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="e42f7-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e42f7-105">Bu örnekte [kullanılan dosyalar, konusunda nasıl yapılır: Bir metin dosyasına](./how-to-write-to-a-text-file.md)yazın.</span><span class="sxs-lookup"><span data-stu-id="e42f7-105">The files that are used in this example are created in the topic [How to: Write to a Text File](./how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e42f7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e42f7-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e42f7-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e42f7-107">Compiling the Code</span></span>  
 <span data-ttu-id="e42f7-108">Kodu kopyalayın ve bir C# konsol uygulamasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e42f7-108">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="e42f7-109">Metin dosyalarını [şu şekilde kullanarak kullanmıyorsanız: Bir metin dosyasına](./how-to-write-to-a-text-file.md)yazın, `ReadAllText` bağımsız değişkenini `ReadAllLines` bilgisayarınızdaki uygun yol ve dosya adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e42f7-109">If you are not using the text files from [How to: Write to a Text File](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e42f7-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="e42f7-110">Robust Programming</span></span>  
 <span data-ttu-id="e42f7-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="e42f7-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e42f7-112">Dosya yok veya belirtilen konumda yok.</span><span class="sxs-lookup"><span data-stu-id="e42f7-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="e42f7-113">Dosya adının yolunu ve yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e42f7-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e42f7-114">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e42f7-114">.NET Framework Security</span></span>  
 <span data-ttu-id="e42f7-115">Dosyanın içeriğini belirlemekte bir dosyanın adına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="e42f7-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="e42f7-116">Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e42f7-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42f7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e42f7-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="e42f7-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e42f7-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e42f7-119">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e42f7-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
