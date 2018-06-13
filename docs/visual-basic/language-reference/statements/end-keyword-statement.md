---
title: Son &lt;anahtar sözcüğü&gt; deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 8137434bfd8c26144d78b1761b784cdba4894eaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605270"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>Son &lt;anahtar sözcüğü&gt; deyimi (Visual Basic)
Bir ek anahtar sözcüğüyle izlendiğinde, bu anahtar tarafından sunulan deyimi blok tanımını sonlandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## <a name="parts"></a>Bölümler  
 `End`  
 Gerekli. Programlama öğesi tanımını sonlandırır.  
  
 `AddHandler`  
 Sonlandırmak için gerekli bir `AddHandler` eşleşen bir başlamış erişimcisi `AddHandler` özel deyiminde [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Class`  
 Eşleşen bir başlamış bir sınıf tanımı sonlandırmak için gerekli [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md).  
  
 `Enum`  
 Eşleşen bir başlamış bir numaralandırma tanımı sonlandırmak için gerekli [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 `Event`  
 Sonlandırmak için gerekli bir `Custom` eşleşen bir başlamış olay tanımı [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Function`  
 Sonlandırmak için gerekli bir `Function` eşleşen bir başlamış yordamı tanımı [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md). Yürütme karşılaşırsa bir `End``Function` deyimi, Denetim çağıran kodu döndürür.  
  
 `Get`  
 Sonlandırmak için gerekli bir `Property` eşleşen bir başlamış yordamı tanımı [alma deyimi](../../../visual-basic/language-reference/statements/get-statement.md). Yürütme karşılaşırsa bir `End``Get` deyimi, özelliğin değerini isteyen deyimi denetimini döndürür.  
  
 `If`  
 Sonlandırmak için gerekli bir `If`... `Then`... `Else` engelleme eşleşen bir başlamış tanımı `If` deyimi. Bkz: [varsa... Then... Else deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md).  
  
 `Interface`  
 Eşleşen bir başlamış bir arabirim tanımı sonlandırmak için gerekli [arabirimi deyimi](../../../visual-basic/language-reference/statements/interface-statement.md).  
  
 `Module`  
 Eşleşen bir başlamış bir modül tanımı sonlandırmak için gerekli [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md).  
  
 `Namespace`  
 Eşleşen bir başlamış bir ad alanı tanımını sonlandırmak için gerekli [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md).  
  
 `Operator`  
 Eşleşen bir başlamış bir işleç tanımı sonlandırmak için gerekli [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 `Property`  
 Eşleşen bir başlamış özellik tanımı sonlandırmak için gerekli [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md).  
  
 `RaiseEvent`  
 Sonlandırmak için gerekli bir `RaiseEvent` eşleşen bir başlamış erişimcisi `RaiseEvent` özel deyiminde [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `RemoveHandler`  
 Sonlandırmak için gerekli bir `RemoveHandler` eşleşen bir başlamış erişimcisi `RemoveHandler` özel deyiminde [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Select`  
 Sonlandırmak için gerekli bir `Select`... `Case` engelleme eşleşen bir başlamış tanımı `Select` deyimi. Bkz: [seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
 `Set`  
 Sonlandırmak için gerekli bir `Property` eşleşen bir başlamış yordamı tanımı [Set deyimi](../../../visual-basic/language-reference/statements/set-statement.md). Yürütme karşılaşırsa bir `End``Set` deyimi, özelliğin değerini ayarlama deyimi denetimini döndürür.  
  
 `Structure`  
 Eşleşen bir başlamış bir yapı tanımı sonlandırmak için gerekli [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md).  
  
 `Sub`  
 Sonlandırmak için gerekli bir `Sub` eşleşen bir başlamış yordamı tanımı [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md). Yürütme karşılaşırsa bir `End``Sub` deyimi, Denetim çağıran kodu döndürür.  
  
 `SyncLock`  
 Sonlandırmak için gerekli bir `SyncLock` engelleme eşleşen bir başlamış tanımı `SyncLock` deyimi. Bkz: [SyncLock deyimi](../../../visual-basic/language-reference/statements/synclock-statement.md).  
  
 `Try`  
 Sonlandırmak için gerekli bir `Try`... `Catch`... `Finally` engelleme eşleşen bir başlamış tanımı `Try` deyimi. Bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 `While`  
 Sonlandırmak için gerekli bir `While` döngü eşleşen bir başlamış tanımı `While` deyimi. Bkz: [sırada... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md).  
  
 `With`  
 Sonlandırmak için gerekli bir `With` engelleme eşleşen bir başlamış tanımı `With` deyimi. Bkz: [ile... End With deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="remarks"></a>Açıklamalar  
 [End deyimi](../../../visual-basic/language-reference/statements/end-statement.md), yürütme hemen bir ek anahtar sözcüğü sonlandırır.  
  
 Sayı işareti önlerine (`#`), `End` anahtar sözcüğü karşılık gelen yönergesi tarafından sunulan önişlem bir blok sona erer.  
  
 `#End`  
 Gerekli. Önişlem blok tanımını sonlandırır.  
  
 `#ExternalSource`  
 Eşleşen bir başlamış bir dış kaynağa bloğu sonlandırmak için gerekli [#ExternalSource yönergesi](../../../visual-basic/language-reference/directives/externalsource-directive.md).  
  
 `#If`  
 Eşleşen bir başlamış koşullu derleme bloğunu sonlandırmak için gerekli `#If` yönergesi. Bkz: [#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md).  
  
 `#Region`  
 Eşleşen bir başladı Kaynak bölgesi bloğunu sonlandırmak için gerekli [#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md).  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 `End` Bir ek anahtar sözcüğü olmadan deyimi desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
