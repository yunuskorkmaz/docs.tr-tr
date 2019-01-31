---
title: End <keyword> Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 96dc8ce6b0d3b7545f5caeef43358936e426f566
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273536"
---
# <a name="end-keyword-statement-visual-basic"></a>Son \<anahtar sözcüğü > deyimi (Visual Basic)

Ek bir anahtar sözcüğe göre ve ardından, bu anahtar sözcüğü tarafından sunulan deyim bloğunu tanımını sonlandırır.

## <a name="syntax"></a>Sözdizimi

```vb
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

|Bölümü|Açıklama|
|---|---|
|`End`|Gerekli. Programlama öğesinin tanımını sonlandırır.|
|`AddHandler`|Sonlandırmak için gerekli bir `AddHandler` başlamış eşleşen bir erişimci `AddHandler` özel deyiminde [Event deyimi](event-statement.md).|
|`Class`|Eşleşen bir başlamış bir sınıf tanımı sonlandırması gerekir [Class deyimi](class-statement.md).|
|`Enum`|Eşleşen bir başlamış bir numaralandırma tanımı sonlandırması gerekir [Enum deyimi](enum-statement.md).|
|`Event`|Sonlandırmak için gerekli bir `Custom` başlamış eşleşen bir olay tanımında [Event deyimi](event-statement.md).|  
|`Function`|Sonlandırmak için gerekli bir `Function` başlamış eşleşen bir yordam tanımında [Function deyimi](function-statement.md). Yürütme karşılaşırsa, bir `End Function` deyimi, denetimi çağrıldığı koda döndürür.|
|`Get`|Sonlandırmak için gerekli bir `Property` başlamış eşleşen bir yordam tanımında [alma deyimi](get-statement.md). Yürütme karşılaşırsa, bir `End Get` deyimi, denetimi özelliğinin değeri isteyen deyime döndürür.|
|`If`|Sonlandırmak için gerekli bir `If`... `Then`... `Else` engelleyecek bir eşleştirerek başlamış tanımı `If` deyimi. Bkz: [varsa... Daha sonra... Else deyimi](if-then-else-statement.md).|
|`Interface`|Eşleşen bir başlamış arabirim tanımı sonlandırması gerekir [Interface deyimi](interface-statement.md).|
|`Module`|Eşleşen bir başlamış bir modül tanımı sonlandırması gerekir [Module deyimi](module-statement.md).|
|`Namespace`|Eşleşen bir başlamış bir ad alanı tanımını sonlandırması gerekir [Namespace deyimi](namespace-statement.md).|
|`Operator`|Eşleşen bir başlamış bir işleç tanımını sonlandırması gerekir [Operator deyimi](operator-statement.md).|
|`Property`|Bir özellik tanımı bir eşleştirerek başlamış sonlandırması gerekir [Property deyimi](property-statement.md).|
|`RaiseEvent`|Sonlandırmak için gerekli bir `RaiseEvent` başlamış eşleşen bir erişimci `RaiseEvent` özel deyiminde [Event deyimi](event-statement.md).|
|`RemoveHandler`|Sonlandırmak için gerekli bir `RemoveHandler` başlamış eşleşen bir erişimci `RemoveHandler` özel deyiminde [Event deyimi](event-statement.md).|
|`Select`|Sonlandırmak için gerekli bir `Select`... `Case` engelleyecek bir eşleştirerek başlamış tanımı `Select` deyimi. Bkz: [seçin... Case deyimi](select-case-statement.md).  
|`Set`|Sonlandırmak için gerekli bir `Property` başlamış eşleşen bir yordam tanımında [bildirimine](set-statement.md). Yürütme karşılaşırsa, bir `End Set` deyimi, denetimi özelliğinin değerini ayarlayan bildirimi için döndürür.  
|`Structure`|Eşleşen bir başlamış bir yapı tanımı sonlandırması gerekir [Structure deyimi](structure-statement.md).  
|`Sub`|Sonlandırmak için gerekli bir `Sub` başlamış eşleşen bir yordam tanımında [Sub deyimi](sub-statement.md). Yürütme karşılaşırsa, bir `End Sub` deyimi, denetimi çağrıldığı koda döndürür.  
|`SyncLock`|Sonlandırmak için gerekli bir `SyncLock` engelleyecek bir eşleştirerek başlamış tanımı `SyncLock` deyimi. Bkz: [SyncLock deyimi](synclock-statement.md).  
|`Try`|Sonlandırmak için gerekli bir `Try`... `Catch`... `Finally` engelleyecek bir eşleştirerek başlamış tanımı `Try` deyimi. Bkz: [deneyin... Catch... Finally deyimini](try-catch-finally-statement.md).  
|`While`|Sonlandırmak için gerekli bir `While` döngü bir eşleştirerek başlamış tanımı `While` deyimi. Bkz: [sırada... End While deyimi](while-end-while-statement.md).  
|`With`| Sonlandırmak için gerekli bir `With` engelleyecek bir eşleştirerek başlamış tanımı `With` deyimi. Bkz: [ile... End With deyimi](with-end-with-statement.md).  
|||
  
## <a name="directives"></a>Yönergeler

Sayı işareti önlerine (`#`), `End` anahtar sözcüğü karşılık gelen yönergesi tarafından tanıtılan ön işleme bloğunu sonlandırır.  

```vb
#End ExternalSource
#End If
#End Region
```

|Bölümü|Açıklama|
|---|---|
|`#End`|Gerekli. Ön işleme bloğunun tanımını sonlandırır.|
|`ExternalSource`|Eşleşen bir başlamış bir dış kaynak blok sonlandırma için gereken [#ExternalSource yönergesi](../directives/externalsource-directive.md).|
|`If`|Eşleşen bir başlamış koşullu derleme bloğunu sonlandırmak için gerekli `#If` yönergesi. Bkz: [#If... Then... #Else yönergeleri](../directives/if-then-else-directives.md).|
|`Region`|Eşleşen bir başlamış kaynak bölge blok sonlandırma için gereken [#Region yönergesi](../directives/region-directive.md).|
|||

## <a name="remarks"></a>Açıklamalar

[End deyimi](end-statement.md), ek bir anahtar sözcüğü yürütme hemen sonlanır.

## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  

`End` Deyimi, bir ek anahtar sözcüğü olmadan desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [End Deyimi](end-statement.md)
