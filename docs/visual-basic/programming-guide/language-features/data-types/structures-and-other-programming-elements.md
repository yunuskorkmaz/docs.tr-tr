---
title: "Yapılar ve Diğer Programlama Öğeleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de343c06ec255d6cb68aa25d733e85385e884769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Yapılar ve Diğer Programlama Öğeleri (Visual Basic)
Diziler, nesneleri ve yordamlarla yanı sıra birbirleri ile birlikte yapıları kullanabilirsiniz. Bu öğeleri tek tek kullandıkça etkileşimler aynı sözdizimini kullanır.  
  
> [!NOTE]
>  Yapı bildirimleri yapısı öğelerinde başlatılamıyor. Yalnızca bir yapı türüne sahip olması için bildirilen bir değişken öğelerine değerler atayabilirsiniz.  
  
## <a name="structures-and-arrays"></a>Yapılar ve diziler  
 Bir yapı bir dizi olarak bir veya daha fazla öğeleri içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 Bir nesne üzerinde bir özellik erişim aynı şekilde bir yapısı içinde bir dizi değerlerini erişin. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Bir dizi yapıları da bildirebilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Bu veri mimarisi bileşenlerine erişmek için aynı kuralları izleyin. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Yapılar ve nesneler  
 Bir yapı bir nesne olarak bir veya daha fazla öğeleri içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Bu tür bildiriminde belirli nesne sınıfını kullanmalısınız yerine `Object`.  
  
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
  
 Önceki örnekte yapısı geçirir *başvuruya göre*, yordamın öğeleri arama kodda değişiklikler etkili şekilde değiştirmenize izin verir. Bu tür değişiklik karşı bir yapı korumak istiyorsanız, tarafından değerini geçirin.  
  
 Ayrıca bir yapısından dönebilirsiniz bir `Function` yordamı. Aşağıdaki örnek bunu göstermektedir.  
  
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
 Yapıları diğer yapıları içerebilir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Bu yöntem, bir modülü farklı bir modülde tanımlanmış bir yapı içinde tanımlanmış bir yapı kapsüllemek için de kullanabilirsiniz.  
  
 Yapıları rasgele derinliği diğer yapıları içerebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Başlangıç veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Bileşik veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Yapıları](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Veri türleri sorunlarını giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Nasıl yapılır: bir yapıyı bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Yapı değişkenleri](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [Yapılar ve sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
