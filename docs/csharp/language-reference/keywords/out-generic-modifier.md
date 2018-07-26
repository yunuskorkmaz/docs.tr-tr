---
title: out (Genel Değiştirici) (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 95ccbe3ab5bf2d326e1154af0b169972a24f7e38
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245092"
---
# <a name="out-generic-modifier-c-reference"></a>out (Genel Değiştirici) (C# Başvurusu)
Genel tür parametreleri için `out` anahtar sözcüğü, tür parametresi birlikte değişken olduğunu belirtir. Kullanabileceğiniz `out` genel arabirimlerde ve temsilcilerde anahtar sözcük.  
  
 Kovaryans genel parametre olarak belirtilenden daha türetilmiş bir tür belirtmenize olanak sağlar. Bu değişken arabirimleri uygulayan sınıflar örtük dönüştürülmesi ve temsilci türlerinin örtük dönüştürme için sağlar. Kovaryans ve kontravaryans başvuru türleri için desteklenir ancak değer türleri için desteklenmiyor.  
  
 Dönüş türü parametresi tarafından belirtilenlerden daha türetilmiş türleri metotlarını bir birlikte değişen türde parametresi olan bir arabirim sağlar. Örneğin, çünkü .NET Framework 4 içinde <xref:System.Collections.Generic.IEnumerable%601>T türü birlikte değişken, bir nesnenin atayabilirsiniz `IEnumerable(Of String)` bir nesne türüne `IEnumerable(Of Object)` herhangi bir özel dönüştürme yöntemini kullanmadan türü.  
  
 Birlikte değişen bir temsilci, aynı türden, ancak daha fazla türetilmiş bir genel tür parametresi ile başka bir temsilci atanabilir.  
  
 Daha fazla bilgi için [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirmek, genişletin ve bir değişken genel arabirim uygulamak gösterilmektedir. Ayrıca, birlikte değişen bir arabirimi uygulayan sınıflar için örtük dönüştürme kullanmayı gösterir.  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 Genel arabiriminin tür parametresi aşağıdaki koşulları karşılıyorsa, birlikte değişken bildirilebilir:  
  
-   Tür parametresi yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız bir türü olarak kullanılmaz.  
  
    > [!NOTE]
    >  Bu kuralın tek istisnası yoktur. Birlikte değişen bir arabirimde bir yöntem parametresi olarak bir değişken karşıtı Genel temsilci varsa, birlikte değişken türünde genel tür parametre olarak bu metot temsilcisi için kullanabilirsiniz. Birlikte değişken hakkında daha fazla bilgi ve değişken karşıtı genel temsilciler [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   Tür parametresi, arabirim yöntemleri için genel bir kısıtlama kullanılmaz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirme, oluşturma ve birlikte değişken temsilci çağırma gösterilmektedir. Ayrıca, örtük olarak temsilci türleri dönüştürme yapılacağını gösterir.  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 Yalnızca bir yöntem dönüş türü kullanılan ve kullanılmayan yöntem bağımsız değişkenleri için genel bir temsilci türü birlikte değişken olarak bildirilebilir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)
