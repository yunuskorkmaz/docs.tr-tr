---
title: Dosya sisteminden bir XML ağacını doldurma-LINQ to XML
description: C# veya Visual Basic bir XML ağacının dosya sisteminden nasıl doldurulacağını öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: 6b0307aca9c9075120021967c08efcad8b595653
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553900"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-linq-to-xml"></a><span data-ttu-id="20c48-103">Dosya sisteminden bir XML ağacını doldurma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="20c48-103">How to populate an XML tree from the file system (LINQ to XML)</span></span>

<span data-ttu-id="20c48-104">XML ağaçlarının ortak ve yararlı bir uygulaması, hiyerarşik ad-değer veri deposu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20c48-104">A common and useful application of XML trees is as a hierarchical name-value data store.</span></span> <span data-ttu-id="20c48-105">Bir XML ağacını hiyerarşik verilerle doldurabilir ve sonra sorgulayabilir, dönüştürebilir ve gerekirse serileştirin.</span><span class="sxs-lookup"><span data-stu-id="20c48-105">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="20c48-106">Bu kullanım için, ad alanları ve boşluk davranışı gibi XML 'e özgü semantik birçoğu önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="20c48-106">For this use, many of the XML-specific semantics, such as namespaces and white space behavior, aren't important.</span></span> <span data-ttu-id="20c48-107">Bunun yerine, XML ağacını küçük, bellek içi, tek kullanıcılı hiyerarşik veritabanı olarak kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="20c48-107">Instead, you're using the XML tree as a small, in-memory, single-user hierarchical database.</span></span>

## <a name="example-populate-an-xml-tree-and-then-query-it"></a><span data-ttu-id="20c48-108">Örnek: bir XML ağacını doldurun ve ardından sorgulayın</span><span class="sxs-lookup"><span data-stu-id="20c48-108">Example: Populate an XML tree and then query it</span></span>

<span data-ttu-id="20c48-109">Aşağıdaki örnek, bir XML ağacını yerel dosya sistemindeki dosyalarla ilgili verilerle doldurmak için özyineleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="20c48-109">The following example uses recursion to populate an XML tree with data about the files in the local file system.</span></span> <span data-ttu-id="20c48-110">Ardından, tüm dosya boyutlarının toplamı olan ağacı sorgular.</span><span class="sxs-lookup"><span data-stu-id="20c48-110">It then queries the tree, totalling all the file sizes.</span></span>

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

```vb
Module Module1
    Function CreateFileSystemXmlTree(ByVal source As String) As XElement
        Dim di As DirectoryInfo = New DirectoryInfo(source)
        Return <Dir Name=<%= di.Name %>>
                   <%= From d In Directory.GetDirectories(source) _
                       Select CreateFileSystemXmlTree(d) %>
                   <%= From fi In di.GetFiles() _
                       Select <File>
                                  <Name><%= fi.Name %></Name>
                                  <Length><%= fi.Length %></Length>
                              </File> %>
               </Dir>
    End Function

    Sub Main()
        Dim fileSystemTree As XElement = CreateFileSystemXmlTree("C:/Tmp")
        Console.WriteLine(fileSystemTree)
        Console.WriteLine("------")
        Dim totalFileSize As Long = _
            ( _
                From f In fileSystemTree...<File> _
                Select CLng(f.<Length>(0)) _
            ).Sum()
        Console.WriteLine("Total File Size:{0}", totalFileSize)
    End Sub
End Module
```

<span data-ttu-id="20c48-111">Örnek aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="20c48-111">The example produces output similar to the following:</span></span>

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
