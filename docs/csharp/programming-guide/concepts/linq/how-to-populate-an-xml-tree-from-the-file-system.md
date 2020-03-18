---
title: Dosya sisteminden bir XML ağacı nasıl doldurulur (C#)
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: beb44be1a787fa09b091aa48022dbb5b10c4632b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345779"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="27266-102">Dosya sisteminden bir XML ağacı nasıl doldurulur (C#)</span><span class="sxs-lookup"><span data-stu-id="27266-102">How to populate an XML tree from the file system (C#)</span></span>
<span data-ttu-id="27266-103">XML ağaçlarının yaygın ve yararlı bir uygulaması hiyerarşik bir ad/değer veri deposu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="27266-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="27266-104">Bir XML ağacını hiyerarşik verilerle doldurabilir ve sorgulayabilir, dönüştürebilir ve gerekirse seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27266-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="27266-105">Bu kullanım senaryosunda, ad alanları ve beyaz alan davranışı gibi XML'e özgü semantiklerin çoğu önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="27266-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="27266-106">Bunun yerine, XML ağacını küçük, bellekte tek kullanıcı hiyerarşik veritabanı olarak kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="27266-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27266-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="27266-107">Example</span></span>  
 <span data-ttu-id="27266-108">Aşağıdaki örnek, özyineleme kullanarak yerel dosya sisteminden bir XML ağacını doldurur.</span><span class="sxs-lookup"><span data-stu-id="27266-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="27266-109">Daha sonra, ağaçtaki tüm dosyaların boyutlarını hesaplayarak ağacı sorgular.</span><span class="sxs-lookup"><span data-stu-id="27266-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```csharp  
class Program  
{  
    static XElement CreateFileSystemXmlTree(string source)  
    {  
        DirectoryInfo di = new DirectoryInfo(source);  
        return new XElement("Dir",  
            new XAttribute("Name", di.Name),  
            from d in Directory.GetDirectories(source)  
            select CreateFileSystemXmlTree(d),  
            from fi in di.GetFiles()  
            select new XElement("File",  
                new XElement("Name", fi.Name),  
                new XElement("Length", fi.Length)  
            )  
        );  
    }  
  
    static void Main(string[] args)  
    {  
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");  
        Console.WriteLine(fileSystemTree);  
        Console.WriteLine("------");  
        long totalFileSize =  
            (from f in fileSystemTree.Descendants("File")  
             select (long)f.Element("Length")).Sum();  
        Console.WriteLine("Total File Size:{0}", totalFileSize);  
    }  
}  
```  
  
 <span data-ttu-id="27266-110">Bu örnek, aşağıdakilere benzer çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="27266-110">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
