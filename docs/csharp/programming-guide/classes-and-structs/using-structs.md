---
title: Yapıları kullanma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 4cfb3b184491e42194204899e26d7f1966a68427
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595994"
---
# <a name="using-structs-c-programming-guide"></a>Yapıları Kullanma (C# Programlama Kılavuzu)
`struct` Türü `Point`, ve`Rectangle`gibi hafif nesneleri temsil etmek için uygundur. `Color` Bir noktayı [Otomatik uygulanmış özelliklerle](./auto-implemented-properties.md)bir [sınıf](../../language-reference/keywords/class.md) olarak temsil etmek uygun olsa da, bazı senaryolarda bir [Yapı](../../language-reference/keywords/struct.md) daha verimli olabilir. Örneğin, 1000 `Point` nesnelerinin bir dizisini bildirirseniz, her bir nesneye başvurmak için ek bellek ayırabilirsiniz; bu durumda, bir yapı daha pahalı olacaktır. .NET Framework adlı <xref:System.Drawing.Point>bir nesne içerdiğinden, bu örnekteki yapı bunun yerine "CoOrds" olarak adlandırılmıştır.  
  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 Bir struct için varsayılan (parametresiz) bir Oluşturucu tanımlamak hatadır. Bir yapı gövdesinde örnek alanı başlatmak da bir hatadır. Yalnızca parametreli bir oluşturucuyu, örtük, parametresiz oluşturucuyu, [nesne başlatıcısını](./object-and-collection-initializers.md)kullanarak veya yapı oluşturulduktan sonra üyelere ayrı ayrı erişerek, dışarıdan erişilebilen yapı üyelerini başlatabilirsiniz. Herhangi bir özel veya başka şekilde erişilemeyen üye, oluşturucuların yalnızca kullanımını gerektirir.
  
 [New](../../language-reference/operators/new-operator.md) işlecini kullanarak bir struct nesnesi oluşturduğunuzda, oluşturulur ve uygun Oluşturucu [oluşturucunun imzasına](./constructors.md#constructor-syntax)göre çağırılır. Sınıfların aksine, yapılar `new` işleci kullanılmadan oluşturulabilir. Böyle bir durumda, bir Oluşturucu çağrısı yoktur ve bu da ayırmayı daha verimli hale getirir. Ancak alanlar atanmamış olarak kalır ve tüm alanlar başlatılana kadar nesne kullanılamaz. Bu, özellikler aracılığıyla değerleri almak veya ayarlamak için bir değer içerir.

 Parametresiz oluşturucuyu kullanarak bir struct nesnesi örneği oluşturursanız, tüm Üyeler [varsayılan değerlerine](../../language-reference/keywords/default-values-table.md)göre atanır.
  
 Bir yapı için parametrelere sahip bir Oluşturucu yazarken, tüm üyeleri açık olarak başlatmalısınız; Aksi takdirde bir veya daha fazla üye atanmamış olarak kalır ve yapı birimi CS0171, derleyici hatası üretirken kullanılamaz.  
  
 Sınıflar için olduğu gibi yapılar için devralma yoktur. Yapı, başka bir struct veya sınıftan devralınabilir ve bir sınıfın temeli olamaz. Ancak yapılar, temel sınıftan <xref:System.Object>devralınır. Bir struct, arabirimler uygulayabilir ve tam olarak sınıfların yaptığı şekilde yapılır.  
  
 Anahtar sözcüğünü `struct`kullanarak bir sınıfı bildiremezsiniz. İçinde C#, sınıflar ve yapılar anlamsal olarak farklıdır. Yapı bir değer türüdür, ancak bir sınıf bir başvuru türüdür. Daha fazla bilgi için bkz. [değer türleri](../../language-reference/keywords/value-types.md).  
  
 Başvuru türü semantiklerine ihtiyacınız yoksa, bunun yerine bir yapı olarak bildirirseniz küçük bir sınıf sistem tarafından daha verimli bir şekilde işlenebilir.  
  
## <a name="example-1"></a>Örnek 1  
  
### <a name="description"></a>Açıklama  
 Bu örnek, `struct` başlatma, hem varsayılan hem de parametreli oluşturucular kullanılarak gösterilmektedir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]  
  
## <a name="example-2"></a>Örnek 2  
  
### <a name="description"></a>Açıklama  
 Bu örnek, yapılar için benzersiz olan bir özelliği gösterir. `new` İşleci kullanmadan bir CoOrds nesnesi oluşturur. Sözcüğü `struct` kelimeyle `class`değiştirirseniz, program derlenmeyecektir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Yapılar](./structs.md)
