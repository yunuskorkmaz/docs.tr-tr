---
title: Anonim Tür Tanımı (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: e74b4c7298a80f724031cc4ac1feb49ebae8f7cb
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975621"
---
# <a name="anonymous-type-definition-visual-basic"></a>Anonim Tür Tanımı (Visual Basic)
Anonim bir türün bir örneği bildirimine yanıt olarak, derleyicinin türü için belirtilen özellikleri içeren yeni bir sınıf tanımı oluşturur.  
  
## <a name="compiler-generated-code"></a>Derleyicinin ürettiği kodu  
 Aşağıdaki tanımını `product`, derleyici özellikleri içeren yeni bir sınıf tanımı oluşturur `Name`, `Price`, ve `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]  
  
 Sınıf tanımı aşağıdaki gibi özellik tanımları içerir. Var olduğuna dikkat edin hiçbir `Set` anahtar özellikleri için yöntemi. Anahtar özelliklerin değerlerini salt okunurdur.  
  
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
  
 Ayrıca, varsayılan bir oluşturucu anonim tür tanımlarını içerir. Parametreler gerektiren oluşturuculara izin verilmez.  
  
 Tür tanımı, bir anonim tür bildirimi en az bir anahtar özellik içeriyorsa, devralınan üç üyeleri geçersiz kılar <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>. Anahtar özellik, yalnızca bildirilmişse <xref:System.Object.ToString%2A> geçersiz kılınır. Geçersiz kılmalar, aşağıdaki işlevleri sağlar:  
  
-   `Equals` döndürür `True` iki anonim tür örnekleri aynı örneği varsa ya da aşağıdaki koşulları karşıladıkları:  
  
    -   Özellikleri aynı sayıda sahiptirler.  
  
    -   Özellikler aynı sırada aynı ada sahip bildirilir ve aynı tür çıkarımı yapılan. Adı karşılaştırmalar büyük küçük harfe duyarlı değildir.  
  
    -   Özellikleri en az biri olan bir anahtar özellik ve `Key` anahtar sözcüğü, aynı özelliklerine uygulanır.  
  
    -   Anahtar özellikler karşılık gelen her çift karşılaştırması döndürür `True`.  
  
     Örneğin, aşağıdaki örnekte, `Equals` döndürür `True` yalnızca `employee01` ve `employee08`. Her satır neden yeni örnek eşleşmiyor nedenini belirtir. önceki yorumun `employee01`.  
  
     [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]  
  
-   `GetHashcode` uygun şekilde benzersiz bir GetHashCode algoritması sağlar. Algoritması yalnızca anahtar özellikler karma kodunu hesaplamak için kullanır.  
  
-   `ToString` Aşağıdaki örnekte gösterildiği gibi bitişik özellik değerleri, bir dize döndürür. Hem anahtar hem de anahtar olmayan özellikler dahil edilir.  
  
     [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]  
  
 Anonim bir türün açıkça adlandırılmış özellikleri ile oluşturulan bu yöntemleri çakışamaz. Diğer bir deyişle, kullanamazsınız `.Equals`, `.GetHashCode`, veya `.ToString` adlı bir özelliği için.  
  
 En az bir içeren anonim tür tanımlarını anahtar özellik de uygulama <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimi, burada `T` anonim tür türüdür.  
  
> [!NOTE]
>  Anonim türde bildirimlerden, yalnızca aynı bütünleştirilmiş kodda ortaya özelliklerini aynı ada sahip ve aynı tür çıkarımı yapılan, özellikler aynı sırada bildirilir ve aynı özellikleri anahtar özellikler işaretlendi, anonim türdeki oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
