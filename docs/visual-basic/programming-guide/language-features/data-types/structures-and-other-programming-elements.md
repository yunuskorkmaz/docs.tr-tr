---
title: Yapılar ve Diğer Programlama Öğeleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: a943bbdec617ba6c95685df3a4fcdb36b52def22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819115"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Yapılar ve Diğer Programlama Öğeleri (Visual Basic)
Yapılar, diziler, nesneleri ve yordamları yanı sıra birbirleri ile birlikte kullanabilirsiniz. Bu öğeleri ayrı ayrı olarak etkileşimleri aynı sözdizimini kullanır.  
  
> [!NOTE]
>  Yapı öğeleri yapısı bildiriminde başlatılamıyor. Yalnızca yapısı türü olarak bildirilmiş bir değişken öğelerine değerler atayabilirsiniz.  
  
## <a name="structures-and-arrays"></a>Yapıları ve diziler  
 Bir yapının bir veya daha fazla alt öğeleri olarak bir dizi içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 Bir yapı içinde bir dizi değerlerini, bir nesne üzerinde bir özelliği aynı şekilde erişin. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Ayrıca, bir dizi yapıları bildirebilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Bu veri mimarisine bileşenlerine erişmek için bu kuralların izleyin. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Yapıları ve nesneler  
 Bir yapının bir nesne bir veya daha fazla alt öğeleri olarak içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Böyle bir bildirim belirli nesne sınıfı kullanmanız gereken yerine `Object`.  
  
## <a name="structures-and-procedures"></a>Yapılar ve yordamları  
 Bir yordam bağımsız değişkeni bir yapı geçirebilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 Yukarıdaki örnekte yapısı geçirir *başvuruya göre*, yordamı çağıran kod değişiklikler etkili şekilde öğeleri değiştirin sağlar. Bir yapı bu tür değişiklik karşı korumak istiyorsanız, değere göre geçirin.  
  
 Ayrıca bir yapısından döndürebilir bir `Function` yordamı. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a>Yapıları içindeki yapıları  
 Yapılar, diğer yapılar içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 Ayrıca, farklı bir modülde tanımlanmış bir yapı içinde bir modülde tanımlanmış bir yapı kapsüllemek için bu tekniği kullanabilirsiniz.  
  
 Yapılar için rastgele bir derinlik diğer yapılar içerebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Yapı Değişkenleri](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Yapılar ve Sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
