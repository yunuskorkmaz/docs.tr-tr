---
title: 'Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: 6e02675a2a895add245d3c2e40305a0417fdf429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)
Nesneler biçimli olduğundan türetilmiş bir tür tutmak için bir temel sınıf türünde bir değişken için mümkündür. Türetilen türün yöntemi erişmek için türetilmiş bir tür değerine geri dönüştürmek gereklidir. Ancak, basit bir girişiminde atma riskini bu gibi durumlarda cast oluşturur bir <xref:System.InvalidCastException>. Diğer bir deyişle neden C# sağlar [olan](../../../csharp/language-reference/keywords/is.md) ve [olarak](../../../csharp/language-reference/keywords/as.md) işleçler. Bir özel durum oluşturulmasına neden olmadan bir cast başarılı olup olmadığını sınamak için aşağıdaki işleçleri kullanabilirsiniz. Genel olarak, `as` işleci olduğundan daha verimli cast başarıyla yapılabilmesi için gerçekten cast değeri döndürür. `is` İşleci bir Boole değeri döndürür. Bu nedenle yalnızca bir nesnenin türünü belirlemek istiyorsanız ancak aslında cast gerekmez kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler nasıl kullanılacağını `is` ve `as` başka bir özel durum atma riski olmadan için bir başvuru cast işleçleri yazın. Bu örnek ayrıca nasıl kullanılacağını gösterir `as` boş değer atanabilen değer türleri olan işleci.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Boş Değer Atanabilir Tipler](../../../csharp/programming-guide/nullable-types/index.md)
