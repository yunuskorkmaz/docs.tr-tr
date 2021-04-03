---
title: Statik oluşturucular-C# Programlama Kılavuzu
description: C# ' de statik bir Oluşturucu statik verileri başlatır veya yalnızca bir kez yapılan bir eylem gerçekleştirir. İlk örnek oluşturulmadan veya statik üyelere başvurulmadan önce çalışır.
ms.date: 03/30/2021
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.openlocfilehash: f7ab97c3723c04b9d442daabb85f8d16967eb0e4
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106123008"
---
# <a name="static-constructors-c-programming-guide"></a>Statik Oluşturucular (C# Programlama Kılavuzu)

Statik bir Oluşturucu herhangi bir [statik](../../language-reference/keywords/static.md) veriyi başlatmak veya yalnızca bir kez gerçekleştirilmesi gereken belirli bir eylemi gerçekleştirmek için kullanılır. İlk örnek oluşturulmadan veya herhangi bir statik üyeye başvurulmadan önce bu otomatik olarak çağrılır.  
  
 [!code-csharp[SimpleClass#1](snippets/static-constructors/Program.cs#1)]

## <a name="remarks"></a>Açıklamalar

Statik oluşturucular aşağıdaki özelliklere sahiptir:  
  
- Statik Oluşturucu erişim değiştiricileri almaz veya parametrelere sahip değildir.  

- Bir sınıf veya yapı birimi yalnızca bir statik oluşturucuya sahip olabilir.

- Statik oluşturucular devralınamaz veya aşırı yüklenemez.

- Statik bir Oluşturucu doğrudan çağrılamaz ve yalnızca ortak dil çalışma zamanı (CLR) tarafından çağrılabilir. Otomatik olarak çağrılır.

- Programda statik Oluşturucu yürütüldüğünde kullanıcının denetimi yoktur.
  
- Statik Oluşturucu otomatik olarak çağrılır. İlk örnek oluşturulmadan veya herhangi bir statik üyeye başvurulmadan önce [sınıfı](../../language-reference/keywords/class.md) başlatır. Statik Oluşturucu bir örnek oluşturucudan önce çalışır. Bir olaya atanan statik bir yöntem veya temsilci atandığında, bir türün statik Oluşturucusu çağrılır. Statik alan değişkeni başlatıcıları statik oluşturucunun sınıfında mevcutsa, bunlar sınıf bildiriminde göründükleri metin sırasına göre yürütülür. Başlatıcılar, statik oluşturucunun yürütülmesinden hemen önce çalışır.

- Statik alanları başlatmak için statik bir Oluşturucu sağlamazsanız, tüm statik alanlar varsayılan değer olan [C# türlerinin varsayılan değerlerinde](../../language-reference/builtin-types/default-values.md)listelendiği şekilde başlatılır.
  
- Statik bir Oluşturucu bir özel durum oluşturursa, çalışma zamanı onu ikinci bir kez çağırmaz ve uygulama etki alanının ömrü boyunca tür başlatılmamış olarak kalır. En yaygın olarak, <xref:System.TypeInitializationException> statik bir Oluşturucu bir tür örneklememediğinde veya statik oluşturucu içinde oluşan işlenmeyen bir özel durum için bir özel durum oluşturulur. Kaynak kodunda açıkça tanımlanmayan statik oluşturucular için, sorun giderme ara dil (IL) kodunu denetlemesini gerektirebilir.

- Statik bir oluşturucunun varlığı <xref:System.Reflection.TypeAttributes.BeforeFieldInit> tür özniteliğinin eklenmesini engeller. Bu, çalışma zamanının iyileştirmesini sınırlandırır.

- Olarak belirtilen bir alan `static readonly` , bildiriminin bir parçası olarak veya bir statik oluşturucuda atanabilir. Açık bir statik Oluşturucu gerekli olmadığında, daha iyi çalışma zamanı iyileştirmesi için bir statik Oluşturucu yerine bildiriminde statik alanları başlatın.

- Çalışma zamanı, bir statik Oluşturucuyu tek bir uygulama etki alanında birden çok kez çağırır. Bu çağrı, sınıfın belirli türüne göre kilitli bir bölgede yapılır. Statik oluşturucunun gövdesinde ek kilitleme mekanizması gerekmez. Kilitlenmeleri riskinden kaçınmak için statik oluşturucularda ve başlatıcılarda geçerli iş parçacığını engellemez. Örneğin, görevler, iş parçacıkları, bekleme tanıtıcıları veya olaylar üzerinde beklememeyin, kilitleri alamaz ve paralel döngüler ve paralel LINQ sorguları gibi paralel işlemleri engellemeyi kullanmayın `Parallel.Invoke` .

> [!Note]
> Doğrudan erişilemeyen halde, açık bir statik oluşturucunun varlığı, başlatma özel durumlarının giderilmesi için yardımcı olmak üzere açıklanmalıdır.

### <a name="usage"></a>Kullanım

- Statik oluşturucuların tipik kullanımı, sınıfın bir günlük dosyası kullanıldığı ve oluşturucunun bu dosyaya giriş yazmak için kullanıldığı durumlarda kullanılır.  
- Statik oluşturucular, Oluşturucu yöntemi çağırabilmesini, yönetilmeyen kod için sarmalayıcı sınıflar oluştururken de kullanışlıdır `LoadLibrary` .  

- Statik oluşturucular, tür parametresi kısıtlamaları aracılığıyla derleme zamanında denetlenemeyen tür parametresinde çalışma zamanı denetimlerini zorlamak için de kullanışlı bir yerdir.

## <a name="example"></a>Örnek

 Bu örnekte, sınıfının `Bus` statik bir Oluşturucusu vardır. İlk örneği `Bus` oluşturulduğunda ( `bus1` ), sınıfı başlatmak için statik oluşturucu çağrılır. Örnek çıktı, statik oluşturucunun, iki örneği `Bus` oluşturulsa ve örnek Oluşturucu çalışmadan önce çalışmasına rağmen yalnızca bir kez çalıştığını doğrular.  
  
 [!code-csharp[BusSample#2](snippets/static-constructors/Program.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](./static-classes-and-static-class-members.md)
- [Sonlandırıcılar](./destructors.md)
- [Oluşturucu tasarım yönergeleri](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Güvenlik Uyarısı-CA2121: statik oluşturucular özel olmalıdır](/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
