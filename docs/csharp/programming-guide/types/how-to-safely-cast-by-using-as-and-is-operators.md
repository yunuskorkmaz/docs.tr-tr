---
title: 'Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: de59fb49ca5dbe1282cd828f7d6995dda449d31b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257307"
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)
Nesneler çok biçimli olduğundan türetilmiş bir tür tutmak için bir temel sınıf türünde bir değişken için mümkündür. Türetilen türün örnek yöntemleri erişmek için türetilmiş bir tür değerine geri değerine dönüştürme gereklidir. Ancak, basit bir denemeye atma riskini cast bu gibi durumlarda oluşturur bir <xref:System.InvalidCastException>. Diğer bir deyişle neden C# sağlar [olduğu](../../../csharp/language-reference/keywords/is.md) ve [olarak](../../../csharp/language-reference/keywords/as.md) işleçleri. Bu işleçler, bir özel durum oluşturulmasına neden olmadan bir tür dönüştürme başarılı olup olmadığını test etmek için kullanabilirsiniz. Genel olarak, `as` işleci olduğundan daha verimli cast başarıyla yapılabilir gerçekten atama değeri döndürür. `is` İşleci bir Boole değeri döndürür. Bu nedenle yalnızca bir nesnenin türünü belirlemek istiyorsanız ancak aslında cast gerekmez kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler nasıl kullanılacağını `is` ve `as` operatörlerinin bir başvurudan atama türünü başka bir özel durum riski olmadan. Örnek ayrıca nasıl kullanılacağını gösterir `as` boş değer atanabilen değer türleri ile işleci.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Boş Değer Atanabilir Tipler](../../../csharp/programming-guide/nullable-types/index.md)
