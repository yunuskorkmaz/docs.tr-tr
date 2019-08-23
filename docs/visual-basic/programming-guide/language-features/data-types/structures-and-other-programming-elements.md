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
ms.openlocfilehash: ec65c75fcfd907097f1cd1e0d3092a547272a782
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933243"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Yapılar ve Diğer Programlama Öğeleri (Visual Basic)
Yapıları diziler, nesneler ve yordamlarla birlikte, birbirleriyle de kullanabilirsiniz. Etkileşimler, bu öğeler tek tek kullanıldığı için aynı sözdizimini kullanır.  
  
> [!NOTE]
> Yapı bildiriminde yapı öğelerinden hiçbirini başlatamıyor. Yalnızca bir yapı türü olarak tanımlanmış bir değişkenin öğelerine değerler atayabilirsiniz.  
  
## <a name="structures-and-arrays"></a>Yapılar ve diziler  
 Bir yapı, öğelerinden biri veya daha fazlası olarak bir dizi içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 Bir yapı içindeki bir dizinin değerlerine, bir nesne üzerindeki bir özelliğe erişirken aynı şekilde erişirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Ayrıca, bir yapı dizisi bildirebilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Bu veri mimarisinin bileşenlerine erişmek için aynı kurallara uyun. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Yapılar ve nesneler  
 Bir yapı, bir veya daha fazla öğelerinden oluşan bir nesne içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Bu tür bir bildirimde, `Object`yerine belirli bir nesne sınıfını kullanmanız gerekir.  
  
## <a name="structures-and-procedures"></a>Yapılar ve yordamlar  
 Bir yapıyı yordam bağımsız değişkeni olarak geçirebilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 Önceki örnek, yapıyı *başvuruya göre*geçirir, bu da değişikliklerin çağıran kodda etkili olması için öğelerini değiştirmesine olanak tanır. Bir yapıyı bu değişikliğe karşı korumak istiyorsanız, değere göre geçirin.  
  
 Ayrıca, bir `Function` yordamdan bir yapı da döndürebilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
## <a name="structures-within-structures"></a>Yapılar Içindeki yapılar  
 Yapılar, diğer yapıları içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Bu tekniği, farklı bir modülde tanımlanan bir yapıda bir modülde tanımlanan bir yapıyı kapsüllemek için de kullanabilirsiniz.  
  
 Yapılar, rastgele bir derinlikte diğer yapıları içerebilir.  
  
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
