---
title: "Anonim Tür Tanımı (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8b5b7eba55d719c1482b7224ecffc78b776feb00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-definition-visual-basic"></a>Anonim Tür Tanımı (Visual Basic)
Anonim bir türün bir örneği bildirimine yanıt olarak derleyici türü için belirtilen özellikleri içeren yeni bir sınıf tanımı oluşturur.  
  
## <a name="compiler-generated-code"></a>Derleyicinin ürettiği kodu  
 Aşağıdaki tanımı için `product`, derleyici özellikleri içeren yeni bir sınıf tanımı oluşturur `Name`, `Price`, ve `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 Sınıf tanımı aşağıdakine benzer özellik tanımları içerir. Var olduğuna dikkat edin hiçbir `Set` anahtar özellikleri için yöntem. Anahtar özellik değerlerini salt okunurdur.  
  
```vb  
Public Class $Anonymous1  
    Private _name As String  
    Private _price As Double  
    Private _onHand As Integer  
     Public ReadOnly Property Name() As String  
        Get  
            Return _name  
        End Get  
    End Property  
  
    Public ReadOnly Property Price() As Double  
        Get  
            Return _price  
        End Get  
    End Property  
  
    Public Property OnHand() As Integer  
        Get  
            Return _onHand  
        End Get  
        Set(ByVal Value As Integer)  
            _onHand = Value  
        End Set  
    End Property  
  
End Class  
```  
  
 Ayrıca, varsayılan bir oluşturucu anonim tür tanımlarını içerir. Parametreler gerektiren oluşturucular izin verilmez.  
  
 Anonim tür bildirimi en az bir anahtar özellik içeriyorsa, tür tanımı devralınan üç üyeleri geçersiz kılar <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>. Hiçbir anahtar özellikler, yalnızca bildirilen varsa <xref:System.Object.ToString%2A> geçersiz kılınır. Geçersiz kılmalar aşağıdaki işlevleri sağlar:  
  
-   `Equals`döndürür `True` iki anonim tür örnekleri aynı örneği varsa ya da aşağıdaki koşullara uyan:  
  
    -   Özellikler aynı sayıda sahiptirler.  
  
    -   Özellikler aynı sırada aynı adı taşıyan bildirilir ve aynı türleri çıkarımı yapılan. Adı karşılaştırmaları büyük küçük harfe duyarlı değildir.  
  
    -   Özellikleri en az biri olan bir anahtar özellik ve `Key` anahtar sözcüğü için aynı özellikleri uygulanır.  
  
    -   Anahtar özellikler karşılık gelen her çifti karşılaştırması döndürür `True`.  
  
     Örneğin, aşağıdaki örnekte, `Equals` döndürür `True` yalnızca `employee01` ve `employee08`. Her satırın neden yeni örnek eşleşmiyor nedenini belirtir önce yorum `employee01`.  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   `GetHashcode`uygun şekilde benzersiz GetHashCode algoritma sağlar. Karma kod işlem için yalnızca anahtar özellikler algoritması kullanır.  
  
-   `ToString`Aşağıdaki örnekte gösterildiği gibi birleştirilmiş özellik değeri bir dize döndürür. Anahtar ve anahtar olmayan özellikler dahil edilir.  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 Anonim bir türün açıkça adlandırılmış özellikleri oluşturulan bu yöntemlerle çakışmamalıdır. Diğer bir deyişle, kullanamazsınız `.Equals`, `.GetHashCode`, veya `.ToString` bir özellik adı için.  
  
 En az bir dahil anonim tür tanımları anahtar özelliği de uygulama <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimi, burada `T` anonim tür türüdür.  
  
> [!NOTE]
>  Yalnızca aynı bütünleştirilmiş kodda oluşma, özelliklerinin aynı ada sahip ve aynı türleri çıkarımı yapılan, özellikler aynı sırada bildirilir ve aynı özellikleri anahtar özellik olarak işaretlenmiş, aynı anonim tür anonim türde bildirimlerden oluşturun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Nasıl yapılır: özellik adları ve türlerini anonim türde bildirimlerden çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
