---
title: "Nasıl yapılır: sorgu için bir klasör (LINQ) (Visual Basic) kümesi bayt toplam sayısı"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b200581f4876400727c63e86e3ccf4a44c67914b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Nasıl yapılır: sorgu için bir klasör (LINQ) (Visual Basic) kümesi bayt toplam sayısı
Bu örnek belirtilen bir klasördeki tüm dosyaları ve onun tüm alt klasörleri tarafından kullanılan bayt toplam sayısını almak üzere nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Linq.Enumerable.Sum%2A> Yöntemi, seçilen tüm öğelerin değerini ekler `select` yan tümcesi. Belirtilen dizin ağacındaki en büyük veya en küçük dosya çağırarak almak için bu sorguyu kolayca değiştirebilirsiniz <xref:System.Linq.Enumerable.Min%2A> veya <xref:System.Linq.Enumerable.Max%2A> yöntemi yerine <xref:System.Linq.Enumerable.Sum%2A>.  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Yalnızca belirtilen dizin ağacında bayt sayısını varsa, daha verimli bir veri kaynağı olarak liste koleksiyonu oluşturma için ek yükü doğurur LINQ Sorgu oluşturmadan bunu yapabilirsiniz. LINQ yaklaşım yararlılığı sorguyu daha karmaşık hale geldiğinde veya birden çok sorgu aynı veri kaynağına karşı çalıştırmak sahip olduğunuzda artırır.  
  
 Sorgu dosyası uzunluğu almak için ayrı bir yöntem için çağırır. Sonra başka bir iş parçacığında dosya silinirse, gerçekleştirilecektir olası özel kullanmak için bunu yapar <xref:System.IO.FileInfo> nesne çağrısında oluşturulduğu `GetFiles`. Olsa bile <xref:System.IO.FileInfo> nesnesi zaten oluşturulmuş, özel durumu oluşabilir çünkü bir <xref:System.IO.FileInfo> nesne Yenile deneyecek kendi <xref:System.IO.FileInfo.Length%2A> özelliği erişildiğinde ilk kez en son uzunluğundaki özellik. Try-catch bloğunda sorgu dışında bu işlemi koyarak kodu yan etkileri neden olan sorguları işlemlerinde önleme kuralı izler. Bir uygulama bilinmeyen bir durumda sol değil emin olmak için özel durumlar kullandığında genel olarak, çok dikkatli olunması gerekir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to nesneler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ ve dosya dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
