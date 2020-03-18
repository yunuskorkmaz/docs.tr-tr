---
title: Genel Sınıflar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 1fdfaa833ad32428d341b6f3a61cc7f638036183
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937512"
---
# <a name="generic-classes-c-programming-guide"></a>Genel Sınıflar (C# Programlama Kılavuzu)
Genel sınıflar, belirli bir veri türüne özgü olmayan işlemleri kapsüller. Genel sınıflar için en yaygın kullanım, bağlantılı listeler, karma tablolar, yığınlar, kuyruklar, ağaçlar ve benzeri koleksiyonlarla yapılır. Koleksiyondan madde ekleme ve kaldırma gibi işlemler, depolanan veri türüne bakılmaksızın temelde aynı şekilde gerçekleştirilir.  
  
 Toplama sınıfları gerektiren çoğu senaryoda, önerilen yaklaşım .NET sınıf kitaplığında sağlananları kullanmaktır. Bu sınıfları kullanma hakkında daha fazla bilgi için [.NET'teki Genel Koleksiyonlar'a](../../../standard/generics/collections.md)bakın.  
  
 Genellikle, varolan bir somut sınıfla başlayarak ve genelleme ve kullanılabilirlik en uygun dengeye ulaşana kadar türleri teker teker tür parametrelerine dönüştürerek genel sınıflar oluşturursunuz. Kendi genel sınıflarınızı oluştururken önemli noktalar şunlardır:  
  
- Tür parametrelerine genelleme yapmak için hangi türleri.  
  
     Kural olarak, parametrenize ne kadar çok tür varsa, kodunuz o kadar esnek ve yeniden kullanılabilir hale gelir. Ancak, çok fazla genelleme diğer geliştiriciler için okumak veya anlamak zor kod oluşturabilirsiniz.  
  
- Tür parametrelerine uygulanacak kısıtlamalar nelerdir [(Bkz. Tür Parametreleri Üzerindeki Kısıtlamalar).](./constraints-on-type-parameters.md)  
  
     İyi bir kural, yine de işlemeniz gereken türleri işlemenize izin verecek mümkün olan maksimum kısıtlamaları uygulamaktır. Örneğin, genel sınıfınızın yalnızca başvuru türleri ile kullanılmak üzere tasarlandığını biliyorsanız, sınıf kısıtlamasını uygulayın. Bu, sınıfınızın değer türleri ile istenmeyen kullanımını önler ve `as` işleci `T`üzerinde kullanmanızı ve null değerlerini denetlemenizi sağlar.  
  
- Genel davranışı temel sınıflara ve alt sınıflara dahil edip etmeme.  
  
     Genel sınıflar temel sınıflar olarak hizmet verebildiği için, genel olmayan sınıflarda olduğu gibi burada da aynı tasarım konuları geçerlidir. Bu konunun ilerleyen saatlerinde genel temel sınıflardan devralma yla ilgili kurallara bakın.  
  
- Bir veya daha fazla genel arabirim uygulayıp uygulamamak.  
  
     Örneğin, genel tabanlı bir koleksiyonda öğeler oluşturmak için kullanılacak bir sınıf tasarlıyorsanız, sınıfınızın türü <xref:System.IComparable%601> nerede `T` olduğu gibi bir arabirim uygulamanız gerekebilir.  
  
 Basit bir genel sınıf örneği için [bkz.](./index.md)  
  
 Tür parametreleri ve kısıtlamaları için kurallar, özellikle devralma ve üye erişilebilirliği ile ilgili genel sınıf davranışı için çeşitli etkileri vardır. Devam etmeden önce, bazı terimleri anlamalısınız. Genel bir `Node<T>,` sınıf istemci kodu için kapalı bir yapıt türü oluşturmak için,`Node<int>`bir tür bağımsız değişkeni belirterek sınıf başvuru olabilir ( . . Alternatif olarak, örneğin genel bir taban sınıfı belirttiğinizde, açık yapılı bir tür (`Node<T>`oluşturmak için tür parametresini belirtilmemiş bırakabilir. Genel sınıflar, beton, kapalı inşa edilmiş veya açık yapılı taban sınıflarından devralınabilir:  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 Genel olmayan, diğer bir deyişle, somut, sınıflar kapalı yapılı taban sınıflarından devralabilir, ancak istemci kodunun anında kullanılabilir şekilde tür bağımsız değişkenini sağlaması için çalışma zamanında hiçbir yol bulunmadığından, açık yapılandırılan sınıflardan veya tür parametrelerinden devralınabilir taban sınıf.  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 Açık yapılandırılan türlerden devralan genel sınıflar, aşağıdaki kodda gösterildiği gibi, devralan sınıf tarafından paylaşılmayan herhangi bir taban sınıf türü parametreleri için tür bağımsız değişkenleri sağlamalıdır:  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 Açık yapılandırılan türlerden devralan genel sınıflar, temel türdeki kısıtlamaların bir üst kümesi olan veya ima eden kısıtlamaları belirtmelidir:  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 Genel türler aşağıdaki gibi birden çok tür parametreleri ve kısıtlamaları kullanabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 Açık yapılı ve kapalı yapılı türler yöntem parametreleri olarak kullanılabilir:  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 Genel bir sınıf bir arabirim uygularsa, bu sınıfın tüm örnekleri bu arabirime döküm olabilir.  
  
 Genel sınıflar değişmez. Başka bir deyişle, bir giriş parametresi `List<BaseClass>`bir , bir ' sağlamak için çalışırsanız `List<DerivedClass>`bir derleme-zaman hatası alırsınız belirtirse .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Tümumeratörlerin Durumunu Kurtarmak](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [Bir Miras Bulmaca, Bölüm Bir](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
