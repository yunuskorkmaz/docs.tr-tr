---
title: 'Nasıl yapılır: Dosyaları (LINQ) uzantıya göre gruplama (C#)'
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: 0b8cb30396a93f5f878c091c4aad3cab9db3f2d4
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584305"
---
# <a name="how-to-group-files-by-extension-linq-c"></a>Nasıl yapılır: Dosyaları (LINQ) uzantıya göre gruplama (C#)
Bu örnek, LINQ Gelişmiş gruplandırma ve sıralama dosya veya klasörleri listelerde işlemleri gerçekleştirmek için nasıl kullanılabileceğini gösterir. Ayrıca bir konsol penceresinde çıktıyı kullanarak sayfa nasıl gösterir <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> yöntemleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu, belirtilen dizin ağacı içeriğini dosya adı uzantısına göre gruplandırmak gösterilmektedir.  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of   
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 Bu program çıktısı, yerel dosya sistemi ve hangi ayrıntılarını bağlı olarak uzun `startFolder` ayarlanır. Tüm sonuçları izlenmesini etkinleştirmek için bu örnekte sonuç gösterilmiştir. Aynı teknikleri, Windows ve Web uygulamaları için uygulanabilir. Bir iç içe bir grup içindeki öğeler kod sayfaları çünkü dikkat `foreach` döngü gereklidir. Bazı ilave bir mantık geçerli konumu listesinde işlem ve disk belleği durdurmak ve programdan çıkmak kullanıcının etkinleştirmek için de mevcuttur. Bu durumda, disk belleği sorgu özgün sorgunun önbelleğe alınan sonuçları karşı çalıştırılır. LINQ to SQL gibi diğer bağlamlarda bu önbelleğe alma gerekli değildir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Oluşturma bir C# konsol uygulama projesi ile `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects'in (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ ve dosya dizinleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
