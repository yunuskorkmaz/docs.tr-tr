---
title: "Out (Genel Değiştirici) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e54504cd65b78846af41692f39899140a6d99b5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="out-generic-modifier-visual-basic"></a>Out (Genel Değiştirici) (Visual Basic)
Genel tür parametreleri için `Out` anahtar sözcük türü eşdeğişken olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kovaryans genel parametresi tarafından belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar. Bu değişken arabirimleri uygulayan sınıfların örtük dönüştürme ve temsilci türleri örtük dönüştürme için sağlar.  
  
 Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Kurallar  
 Kullanabileceğiniz `Out` anahtar sözcüğü genel arabirimler ve temsilciler.  
  
 Bir genel arabiriminde bir tür parametresi aşağıdaki koşullar uymazsa eşdeğişken bildirilebilir:  
  
-   Tür parametresi yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız değişkenleri bir tür olarak kullanılmaz.  
  
    > [!NOTE]
    >  Bu kural için bir istisna vardır. Eşdeğişken arabiriminde karşıtı Genel temsilci bir yöntem parametresi olarak varsa, bu temsilci için genel tür parametresi olarak eşdeğişken türü kullanabilirsiniz. Eşdeğişken hakkında daha fazla bilgi ve karşıtı genel temsilciler [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   Tür parametresi, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz.  
  
 Yalnızca bir yöntemin dönüş türü olarak kullanılır ve yöntem bağımsız değişkenleri için kullanılmaz, genel bir temsilci türü parametresi eşdeğişken olarak bildirilebilir.  
  
 Kovaryans ve kontravaryans referans türleri için desteklenir, ancak değer türlerinde desteklenmez.  
  
 Visual Basic'te temsilci türü belirtmeden eşdeğişken Arabirimlerdeki olaylar bildiremezsiniz. Ayrıca, eşdeğişken arabirimleri sınıfları, numaralandırmaları ve yapıları işleminde içe olamaz, ancak bunlar arabirimleri.  
  
## <a name="behavior"></a>Davranış  
 Tür parametresi tarafından belirtilen daha fazla türetilmiş türler döndürülecek yöntemlerinden eşdeğişken türü parametresine sahip bir arabirim sağlar. Örneğin, çünkü .NET Framework 4'te içinde <xref:System.Collections.Generic.IEnumerable%601>T türü eşdeğişken, bir nesnenin atayabilirsiniz `IEnumerabe(Of String)` bir nesne türüne `IEnumerable(Of Object)` herhangi bir özel dönüştürme yöntem kullanmadan türü.  
  
 Aynı türde, ancak daha fazla türetilmiş genel tür parametresi olan başka bir temsilci eşdeğişken temsilci atanabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirme, genişletmek ve eşdeğişken genel arabirimini uygulayan gösterilmektedir. Ayrıca, eşdeğişken arabirimini uygulayan sınıflar için örtük dönüşüm kullanmayı gösterir.  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirme, oluşturma ve eşdeğişken genel temsilcisi çağırma gösterilmektedir. Örtük dönüştürme temsilci türleri için nasıl kullanabileceğiniz gösterilmektedir.  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
