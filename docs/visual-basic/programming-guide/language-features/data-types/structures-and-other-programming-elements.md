---
title: Yapılar ve Diğer Programlama Öğeleri
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 73d3f999e95c484dff3f5409f2cdb9032b64fe38
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266865"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Yapılar ve Diğer Programlama Öğeleri (Visual Basic)
Yapıları diziler, nesneler ve yordamlarla ve birbiriyle birlikte kullanabilirsiniz. Etkileşimler, bu öğelerin tek tek kullandığı sözdizimini kullanır.  
  
> [!NOTE]
> Yapı bildirimindeki yapı öğelerinden hiçbirini başharfe agiremezsiniz. Değerleri yalnızca bir yapı türüne ait olduğu bildirilen bir değişkenin öğelerine atayabilirsiniz.  
  
## <a name="structures-and-arrays"></a>Yapılar ve Diziler  
 Bir yapı, bir veya daha fazla öğesi olarak bir dizi içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 Bir nesnedeki bir özelliğe eriştiğin gibi bir yapı içindeki dizinin değerlerine erişirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Bir dizi yapıyı da bildirebilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Bu veri mimarisinin bileşenlerine erişmek için aynı kurallara uyarsınız. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Yapılar ve Nesneler  
 Bir yapı, bir nesneyi bir veya daha fazla öğe olarak içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Böyle bir bildirimde belirli bir nesne sınıfı `Object`yerine kullanmalısınız.  
  
## <a name="structures-and-procedures"></a>Yapı ve Prosedürler  
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
  
 Önceki örnek, yordamın öğelerini değiştirmesini sağlayan, arama kodunda değişikliklerin etkili olmasını sağlayan yapıyı *referansla*geçirir. Bir yapıyı bu tür değişikliklere karşı korumak istiyorsanız, değerine göre geçirin.  
  
 Ayrıca bir `Function` yordamdan bir yapı döndürebilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
## <a name="structures-within-structures"></a>Yapıların İçindeki Yapılar  
 Yapılar başka yapılar içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Ayrıca, farklı bir modülde tanımlanan bir yapı içinde tek bir modülde tanımlanan bir yapıyı kapsüllemek için de bu tekniği kullanabilirsiniz.  
  
 Yapılar rasgele bir derinliğe diğer yapıları içerebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türleri Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Nasıl yapılır: Bir Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Yapı Değişkenleri](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Yapılar ve Sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
