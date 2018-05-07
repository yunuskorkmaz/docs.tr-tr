---
title: '&#39;&lt;membername&gt; &#39; devralınan arabirimler arasında belirsiz &#39; &lt;interfacename1&gt; &#39; ve &#39; &lt;interfacename2&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 23d1a11bcee2a4faae40f2683d109d5820ee5f9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39ltmembernamegt39-is-ambiguous-across-the-inherited-interfaces-39ltinterfacename1gt39-and-39ltinterfacename2gt39"></a>&#39;&lt;membername&gt; &#39; devralınan arabirimler arasında belirsiz &#39; &lt;interfacename1&gt; &#39; ve &#39; &lt;interfacename2&gt;&#39;
Arabirimi aynı ada sahip iki veya daha fazla üye birden çok arabirimlerinden devralır.  
  
 **Hata Kimliği:** BC30685  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kullanmak istediğiniz temel arabirim değerine cast; Örneğin:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
