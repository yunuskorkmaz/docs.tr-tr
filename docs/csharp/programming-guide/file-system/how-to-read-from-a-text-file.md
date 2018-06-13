---
title: 'Nasıl yapılır: Metin Dosyasından Okuma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: a42f98a81ff9e9bdbbf6c61554667aa223c7c269
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331678"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="8c792-102">Nasıl yapılır: Metin Dosyasından Okuma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8c792-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="8c792-103">Statik yöntemler kullanarak bu örnek bir metin dosyasının içeriğini okur <xref:System.IO.File.ReadAllText%2A> ve <xref:System.IO.File.ReadAllLines%2A> gelen <xref:System.IO.File?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c792-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="8c792-104">Kullanan bir örnek <xref:System.IO.StreamReader>, bkz: [nasıl yapılır: metin dosyası tek bir çizgi aynı anda okuma](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="8c792-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c792-105">Bu örnekte kullanılan dosyalar konusundaki oluşturulur [nasıl yapılır: bir metin dosyasına yazma](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="8c792-105">The files that are used in this example are created in the topic [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c792-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c792-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c792-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8c792-107">Compiling the Code</span></span>  
 <span data-ttu-id="8c792-108">Kodu kopyalayın ve C# konsol uygulamasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="8c792-108">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="8c792-109">Metin dosyalarını kullanmıyorsanız [nasıl yapılır: bir metin dosyasına yazma](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), bağımsız değişkeni Değiştir `ReadAllText` ve `ReadAllLines` bilgisayarınızda uygun yolu ve dosya adı ile.</span><span class="sxs-lookup"><span data-stu-id="8c792-109">If you are not using the text files from [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8c792-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8c792-110">Robust Programming</span></span>  
 <span data-ttu-id="8c792-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="8c792-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="8c792-112">Dosya yok veya belirtilen konumda yok.</span><span class="sxs-lookup"><span data-stu-id="8c792-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="8c792-113">Yolun ve dosya adının yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8c792-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8c792-114">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8c792-114">.NET Framework Security</span></span>  
 <span data-ttu-id="8c792-115">Dosya içeriğini belirlemek için bir dosya adını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8c792-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="8c792-116">Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8c792-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c792-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c792-117">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="8c792-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8c792-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8c792-119">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8c792-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
