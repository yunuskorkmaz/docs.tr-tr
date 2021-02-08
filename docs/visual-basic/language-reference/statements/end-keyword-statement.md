---
description: 'Daha fazla bilgi edinin: End <keyword> deyiminiz (Visual Basic)'
title: End <keyword> Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: ba21d4ba68a054d77d4f29307d49ed8e82bb6b50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769201"
---
# <a name="end-keyword-statement-visual-basic"></a>End \<keyword> Deyimi (Visual Basic)

Ardından ek bir anahtar sözcük tarafından izlenen, bu anahtar sözcük tarafından tanıtılan bildiri bloğunun tanımını sonlandırır.

## <a name="syntax"></a>Syntax

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

|Bölüm|Description|
|---|---|
|`End`|Gereklidir. Programlama öğesinin tanımını sonlandırır.|
|`AddHandler`|`AddHandler` `AddHandler` Özel bir [olay deyimindeki](event-statement.md)eşleşen bir ifade tarafından başlatılan bir erişimciyi sonlandırmak için gereklidir.|
|`Class`|Eşleşen [sınıf ifadesiyle](class-statement.md)başlatılan bir sınıf tanımını sonlandırmak için gereklidir.|
|`Enum`|Bir sabit listesi tanımını sonlandırmak için, eşleşen bir [enum ifadesiyle](enum-statement.md)başlamış olması gerekir.|
|`Event`|`Custom`Eşleşen bir [olay bildirimiyle](event-statement.md)başlatılan bir olay tanımını sonlandırmak için gereklidir.|  
|`Function`|`Function`Eşleşen bir [işlev ifadesiyle](function-statement.md)başlatılan bir yordam tanımını sonlandırmak için gereklidir. Yürütme bir `End Function` deyimle karşılaşırsa, Denetim çağıran koda geri döner.|
|`Get`|`Property`Eşleşen [Get ifadesiyle](get-statement.md)başlatılan bir yordam tanımını sonlandırmak için gereklidir. Yürütme bir `End Get` deyimle karşılaşırsa denetim, özelliğin değerini isteyen ifadeye döner.|
|`If`|Sonlandırmak için gereklidir `If` .. `Then` . ...`Else` blok tanımı eşleşen bir ifade tarafından başlatıldı `If` . Bkz [.... Sonra... Else bildirisi](if-then-else-statement.md).|
|`Interface`|Eşleşen [arabirim bildirimiyle](interface-statement.md)başlatılan bir arabirim tanımını sonlandırmak için gereklidir.|
|`Module`|Eşleşen bir [Modül ifadesiyle](module-statement.md)başlatılan bir modül tanımını sonlandırmak için gereklidir.|
|`Namespace`|Bir ad alanı tanımını sonlandırmak için eşleşen bir [ad alanı ifadesiyle](namespace-statement.md)başlamış olması gerekir.|
|`Operator`|Eşleşen [Işleç ifadesiyle](operator-statement.md)başlatılan bir operatör tanımını sonlandırmak için gereklidir.|
|`Property`|Eşleşen bir [özellik ifadesiyle](property-statement.md)başlatılan bir özellik tanımını sonlandırmak için gereklidir.|
|`RaiseEvent`|`RaiseEvent` `RaiseEvent` Özel bir [olay deyimindeki](event-statement.md)eşleşen bir ifade tarafından başlatılan bir erişimciyi sonlandırmak için gereklidir.|
|`RemoveHandler`|`RemoveHandler` `RemoveHandler` Özel bir [olay deyimindeki](event-statement.md)eşleşen bir ifade tarafından başlatılan bir erişimciyi sonlandırmak için gereklidir.|
|`Select`|`Select`Eşleşen bir deyimle başlatılan bir... `Case` Block tanımını sonlandırmak için gereklidir `Select` . Bkz [. Select... Case bildirisi](select-case-statement.md).  
|`Set`|`Property`Eşleşen bir [küme ifadesiyle](set-statement.md)başlatılan bir yordam tanımını sonlandırmak için gereklidir. Yürütme bir `End Set` deyimle karşılaşırsa denetim, özelliğin değerini ayarlayarak ifadeye döner.  
|`Structure`|Eşleşen bir [Yapı bildirimiyle](structure-statement.md)başlatılan bir yapı tanımını sonlandırmak için gereklidir.  
|`Sub`|`Sub`Eşleşen bir [Sub ifadesiyle](sub-statement.md)başlatılan bir yordam tanımını sonlandırmak için gereklidir. Yürütme bir `End Sub` deyimle karşılaşırsa, Denetim çağıran koda geri döner.  
|`SyncLock`|`SyncLock`Eşleşen bir deyimle başlatılan bir blok tanımını sonlandırmak için gereklidir `SyncLock` . Bkz. [SyncLock bildirisi](synclock-statement.md).  
|`Try`|Sonlandırmak için gereklidir `Try` .. `Catch` . ...`Finally` blok tanımı eşleşen bir ifade tarafından başlatıldı `Try` . Bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).  
|`While`|`While`Eşleşen bir deyimle başlatılan döngü tanımını sonlandırmak için gereklidir `While` . Bkz.... [ End while bildirisi](while-end-while-statement.md).  
|`With`| `With`Eşleşen bir deyimle başlatılan bir blok tanımını sonlandırmak için gereklidir `With` . Bkz.... [ WITH Ifadesiyle biter](with-end-with-statement.md).  
|||
  
## <a name="directives"></a>Yönergeler

Önünde bir sayı işareti () olduğunda `#` , `End` anahtar sözcüğü karşılık gelen yönerge tarafından tanıtılan bir ön işleme bloğunu sonlandırır.  

```vb
#End ExternalSource
#End If
#End Region
```

|Bölüm|Description|
|---|---|
|`#End`|Gereklidir. Ön işleme bloğunun tanımını sonlandırır.|
|`ExternalSource`|Bir dış kaynak bloğunu, eşleşen bir [#ExternalSource yönergesi](../directives/externalsource-directive.md)tarafından başlatılan sonlandırmak için gereklidir.|
|`If`|Bir eşleşen yönergeyle başlatılan koşullu bir derleme bloğunu sonlandırmak için gereklidir `#If` . Bkz [. #If... Sonra... #Else yönergeleri](../directives/if-then-else-directives.md).|
|`Region`|Eşleşen bir [#Region yönergesi](../directives/region-directive.md)tarafından başlatılan bir kaynak bölgesi bloğunu sonlandırmak için gereklidir.|
|||

## <a name="remarks"></a>Açıklamalar

Ek anahtar sözcük olmadan [End ifadesinin](end-statement.md)yürütülmesi hemen sonlandırılır.

## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  

`End`Ek bir anahtar sözcük olmadan ifade desteklenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [End ekstresi](end-statement.md)
