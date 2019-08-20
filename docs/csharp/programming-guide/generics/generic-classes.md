---
title: Genel sınıflar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 6eb4df4489f4b377c68c5d49d1bf0bb01b835e85
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589773"
---
# <a name="generic-classes-c-programming-guide"></a>Genel Sınıflar (C# Programlama Kılavuzu)
Genel sınıflar, belirli bir veri türüne özgü olmayan işlemleri kapsültir. Genel sınıflar için en yaygın kullanım, bağlantılı listeler, karma tablolar, yığınlar, kuyruklar, ağaçlar vb. gibi koleksiyonlardır. Koleksiyondan öğe ekleme ve kaldırma gibi işlemler, depolanan verilerin türüne bakılmaksızın temelde aynı şekilde gerçekleştirilir.  
  
 Koleksiyon sınıfları gerektiren çoğu senaryo için önerilen yaklaşım, .NET sınıf kitaplığı 'nda sağlananları kullanmaktır. Bu sınıfların kullanımı hakkında daha fazla bilgi için bkz. [.net 'Teki genel Koleksiyonlar](../../../standard/generics/collections.md).  
  
 Genellikle, mevcut bir somut sınıfla başlayarak genel sınıflar oluşturur ve en iyi Genelleştirme ve kullanılabilirlik bakiyesine ulaşana kadar, türleri tek seferde tür parametrelerine değiştirerek. Kendi genel sınıflarınızı oluştururken, önemli noktalara şunlar dahildir:  
  
- Tür parametrelerine genelleştiriedilecek türler.  
  
     Kural olarak, ne kadar çok tür parametreleştirebilirsiniz, kodunuzun daha esnek ve yeniden kullanılabilir hale gelmesi de olur. Ancak, çok fazla Genelleştirme, diğer geliştiricilerin okuması veya anlaşılması zor olan kodlar oluşturabilir.  
  
- Varsa tür parametrelerine uygulanacak kısıtlamalar (bkz. [tür parametrelerine yönelik kısıtlamalar](./constraints-on-type-parameters.md)).  
  
     İşlenmesi gereken türleri işleyebilmeniz için mümkün olan en yüksek kısıtlamaları uygulamak iyi bir kuraldır. Örneğin, genel sınıfınızın yalnızca başvuru türleriyle kullanılması amaçlandığını biliyorsanız, sınıf kısıtlamasını uygulayın. Bu, sınıfınızın değer türleriyle istenmeden kullanımını engeller ve üzerinde `as` `T`işlecini kullanmanıza olanak sağlar ve null değerler olup olmadığını kontrol eder.  
  
- Genel davranışın temel sınıflar ve alt sınıflara göre çarpanının yapılıp yapılmayacağını belirtir.  
  
     Genel sınıflar temel sınıf olarak işlev sağladığından, genel olmayan sınıflarda olduğu gibi aynı tasarım konuları da geçerlidir. Bu konunun ilerleyen kısımlarında genel temel sınıflardan devralma kurallarını inceleyin.  
  
- Bir veya daha fazla genel arabirim uygulanıp etkinleştirilmeyeceğini belirtir.  
  
     Örneğin, genel türler tabanlı bir koleksiyonda öğe oluşturmak için kullanılacak bir sınıf tasarlıyorsanız, sınıfınızın türü olduğu gibi bir arabirim <xref:System.IComparable%601> `T` uygulamanız gerekebilir.  
  
 Basit bir genel sınıf örneği için bkz. Genel türlere [giriş](./index.md).  
  
 Tür parametreleri ve kısıtlamaları için kurallar, özellikle devralma ve üye erişilebilirliği ile ilgili genel sınıf davranışı için çeşitli etkilere sahiptir. Devam etmeden önce bazı terimleri anlamanız gerekir. Bir genel sınıf `Node<T>,` istemci kodu için, bir tür bağımsız değişkeni belirterek, kapalı bir oluşturulmuş tür (`Node<int>`) oluşturmak üzere sınıfına başvurabilir. Alternatif olarak, tür parametresi belirtilmemiş olabilir, örneğin, bir genel temel sınıf belirttiğinizde açık bir oluşturulan tür (`Node<T>`) oluşturabilirsiniz. Genel sınıflar somut, Kapalı oluşturulmuş veya açık oluşturulmuş temel sınıflardan kalýtýmla alabilir:  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 Genel olmayan, diğer bir deyişle, somut, sınıflar, açık oluşturulmuş sınıflardan veya tür parametrelerinden devralınabilir, çünkü bu durum, istemci kodu için çalışma zamanında, temel sınıf.  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 Açık oluşturulmuş türlerden devralan genel sınıflar, aşağıdaki kodda gösterildiği gibi, devralan sınıf tarafından paylaşılmayan herhangi bir temel sınıf türü parametre için tür bağımsız değişkenleri sağlamalıdır:  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 Açık oluşturulmuş türlerden devraldığı genel sınıflar, temel türdeki kısıtlamaların bir üst kümesi veya sayısı olan kısıtlamaları belirtmelidir:  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 Genel türler, birden çok tür parametrelerini ve kısıtlamalarını şu şekilde kullanabilir:  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 Açık oluşturulmuş ve kapalı oluşturulmuş türler, yöntem parametreleri olarak kullanılabilir:  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 Bir genel sınıf bir arabirim uygularsa, bu sınıfın tüm örnekleri bu arabirime eklenebilir.  
  
 Genel sınıflar sabit. Diğer bir deyişle, bir giriş parametresi bir `List<BaseClass>`belirtiyorsa, `List<DerivedClass>`sağlamaya çalışırsanız derleme zamanı hatası alırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Numaralandırıcıların durumunu kaydetme](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)
- [Devralma bulmaca, birinci bölüm](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)
