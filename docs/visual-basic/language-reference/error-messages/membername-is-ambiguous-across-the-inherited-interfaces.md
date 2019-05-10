---
title: "'<membername>', devralınmış '<interfacename1>' ve '<interfacename2>' arabirimleri arasında belirsiz"
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 71f8cb96c9981bbfc55236ea815fa5f5cb0e8aaf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622671"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a>'\<membername >' devralınan arabirimleri arasında belirsiz\<interfacename1 >' ve '\<interfacename2 >'
Arabirimi aynı ada sahip iki veya daha fazla üyesi birden çok arabirimlerinden devralır.  
  
 **Hata Kimliği:** BC30685  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Kullanmak istediğiniz temel arabirim değerine dönüştürme; Örneğin:  
  
    ```  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
