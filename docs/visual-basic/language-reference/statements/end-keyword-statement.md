---
title: End <keyword> Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343744"
---
# <a name="end-keyword-statement-visual-basic"></a>End \<anahtar sözcüğü > deyimin (Visual Basic)

Ardından ek bir anahtar sözcük tarafından izlenen, bu anahtar sözcük tarafından tanıtılan bildiri bloğunun tanımını sonlandırır.

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

|Bölümüyle|Açıklama|
|---|---|
|`End`|Gerekli. Programlama öğesinin tanımını sonlandırır.|
|`AddHandler`|Özel bir [olay deyimindeki](event-statement.md)eşleşen bir `AddHandler` ifadesiyle başlatılan bir `AddHandler` erişimcisini sonlandırmak için gereklidir.|
|`Class`|Eşleşen [sınıf ifadesiyle](class-statement.md)başlatılan bir sınıf tanımını sonlandırmak için gereklidir.|
|`Enum`|Bir sabit listesi tanımını sonlandırmak için, eşleşen bir [enum ifadesiyle](enum-statement.md)başlamış olması gerekir.|
|`Event`|Eşleşen bir [olay bildirimiyle](event-statement.md)başlatılan `Custom` bir olay tanımını sonlandırmak için gereklidir.|  
|`Function`|Eşleşen bir [Işlev ifadesiyle](function-statement.md)başlatılan bir `Function` yordam tanımını sonlandırmak için gereklidir. Yürütme bir `End Function` ifadesiyle karşılaşırsa, Denetim çağıran koda geri döner.|
|`Get`|Eşleşen bir [Get ifadesiyle](get-statement.md)başlatılan `Property` yordam tanımını sonlandırmak için gereklidir. Yürütme bir `End Get` ifadesiyle karşılaşırsa, denetim özelliğin değerini isteyen ifadeye döner.|
|`If`|Eşleşen bir `If` ifadesiyle başlatılan bir `If`...`Then`...`Else` blok tanımını sonlandırmak için gereklidir. Bkz [.... Sonra... Else bildirisi](if-then-else-statement.md).|
|`Interface`|Eşleşen [arabirim bildirimiyle](interface-statement.md)başlatılan bir arabirim tanımını sonlandırmak için gereklidir.|
|`Module`|Eşleşen bir [Modül ifadesiyle](module-statement.md)başlatılan bir modül tanımını sonlandırmak için gereklidir.|
|`Namespace`|Bir ad alanı tanımını sonlandırmak için eşleşen bir [ad alanı ifadesiyle](namespace-statement.md)başlamış olması gerekir.|
|`Operator`|Eşleşen [Işleç ifadesiyle](operator-statement.md)başlatılan bir operatör tanımını sonlandırmak için gereklidir.|
|`Property`|Eşleşen bir [özellik ifadesiyle](property-statement.md)başlatılan bir özellik tanımını sonlandırmak için gereklidir.|
|`RaiseEvent`|Özel bir [olay deyimindeki](event-statement.md)eşleşen bir `RaiseEvent` ifadesiyle başlatılan bir `RaiseEvent` erişimcisini sonlandırmak için gereklidir.|
|`RemoveHandler`|Özel bir [olay deyimindeki](event-statement.md)eşleşen bir `RemoveHandler` ifadesiyle başlatılan bir `RemoveHandler` erişimcisini sonlandırmak için gereklidir.|
|`Select`|`Select`...`Case` blok tanımının eşleşen bir `Select` ifadesiyle başlamış olması gerekir. Bkz [. Select... Case bildirisi](select-case-statement.md).  
|`Set`|Eşleşen bir [küme ifadesiyle](set-statement.md)başlatılan bir `Property` yordam tanımını sonlandırmak için gereklidir. Yürütme bir `End Set` ifadesiyle karşılaşırsa, denetim, özelliğin değerini ayarlayarak ifadeye döner.  
|`Structure`|Eşleşen bir [Yapı bildirimiyle](structure-statement.md)başlatılan bir yapı tanımını sonlandırmak için gereklidir.  
|`Sub`|Eşleşen bir [Sub ifadesiyle](sub-statement.md)başlatılan bir `Sub` yordam tanımını sonlandırmak için gereklidir. Yürütme bir `End Sub` ifadesiyle karşılaşırsa, Denetim çağıran koda geri döner.  
|`SyncLock`|Eşleşen bir `SyncLock` ifadesiyle başlatılan bir `SyncLock` blok tanımını sonlandırmak için gereklidir. Bkz. [SyncLock bildirisi](synclock-statement.md).  
|`Try`|Eşleşen bir `Try` ifadesiyle başlatılan bir `Try`...`Catch`...`Finally` blok tanımını sonlandırmak için gereklidir. Bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).  
|`While`|Eşleşen bir `While` ifadesiyle başlatılan bir `While` döngüsü tanımını sonlandırmak için gereklidir. Bkz.... [ End while bildirisi](while-end-while-statement.md).  
|`With`| Eşleşen bir `With` ifadesiyle başlatılan bir `With` blok tanımını sonlandırmak için gereklidir. Bkz.... [ WITH Ifadesiyle biter](with-end-with-statement.md).  
|||
  
## <a name="directives"></a>Yönergeler

Önünde bir sayı işareti (`#`) olduğunda, `End` anahtar sözcüğü karşılık gelen yönerge tarafından tanıtılan bir ön işleme bloğunu sonlandırır.  

```vb
#End ExternalSource
#End If
#End Region
```

|Bölümüyle|Açıklama|
|---|---|
|`#End`|Gerekli. Ön işleme bloğunun tanımını sonlandırır.|
|`ExternalSource`|Bir dış kaynak bloğunu, eşleşen bir [#ExternalSource yönergesi](../directives/externalsource-directive.md)tarafından başlatılan sonlandırmak için gereklidir.|
|`If`|Eşleşen bir `#If` yönergesi tarafından başlatılan koşullu bir derleme bloğunu sonlandırmak için gereklidir. Bkz [. #If... Sonra... #Else yönergeleri](../directives/if-then-else-directives.md).|
|`Region`|Eşleşen bir [#Region yönergesi](../directives/region-directive.md)tarafından başlatılan bir kaynak bölgesi bloğunu sonlandırmak için gereklidir.|
|||

## <a name="remarks"></a>Açıklamalar

Ek anahtar sözcük olmadan [End ifadesinin](end-statement.md)yürütülmesi hemen sonlandırılır.

## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  

Ek bir anahtar sözcük olmadan `End` deyimleri desteklenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [End Deyimi](end-statement.md)
