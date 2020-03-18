---
title: Statik Yapıcılar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 744bcacbc38299c0ef7d16e814c415ec5caf95dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170123"
---
# <a name="static-constructors-c-programming-guide"></a>Statik Oluşturucular (C# Programlama Kılavuzu)
Statik oluşturucu, [statik](../../language-reference/keywords/static.md) verileri başlatmaya veya yalnızca bir kez gerçekleştirilmesi gereken belirli bir eylemi gerçekleştirmek için kullanılır. İlk örnek oluşturulmadan veya statik üyelere başvurulmadan önce otomatik olarak çağrılır.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a>Açıklamalar
Statik oluşturucular aşağıdaki özelliklere sahiptir:  
  
- Statik bir oluşturucu erişim değiştiriciler almaz veya parametreleri vardır.  

- Bir sınıf veya yapı yalnızca bir statik oluşturucu olabilir.

- Statik yapıcılar kalıtsal veya aşırı yüklenemez.

- Statik bir oluşturucu doğrudan çağrılamaz ve yalnızca ortak dil çalışma zamanı (CLR) tarafından çağrılması amaçlanır. Otomatik olarak çağrılır.

- Kullanıcı, statik oluşturucunun programda ne zaman yürütüldürün üzerinde hiçbir denetimi yoktur.
  
- İlk örnek oluşturulmadan veya statik üyelerbaşvurulmadan önce [sınıfı](../../language-reference/keywords/class.md) başlatmak için statik bir oluşturucu otomatik olarak çağrılır. Statik bir oluşturucu, örnek oluşturucunun önünde çalışır. Bir olaya veya temsilciye atanan statik bir yöntem çağrıldığında, atandığında değil, bir türün statik oluşturucusu çağrılır. Statik alan değişkeni başförü statik yapıcının sınıfında mevcutsa, statik yapıcının yürütülmesinden hemen önce sınıf bildiriminde göründükleri metin sırasına göre yürütülür.

- Statik alanları başlatmak için statik bir oluşturucu sağlamazsanız, tüm statik alanlar [C# türlerinin Varsayılan değerlerinde](../../language-reference/builtin-types/default-values.md)listelenen varsayılan değerlerine başolarak başolarak verilir.
  
- Statik bir oluşturucu bir özel durum atarsa, çalışma zamanı ikinci kez çağrılmaz ve tür, programınızın çalıştırıldığı uygulama etki alanının ömrü boyunca baş harfe dönüşmez. En sık, <xref:System.TypeInitializationException> statik bir oluşturucu bir türü anında oluşturamıyorsa veya statik bir oluşturucu içinde oluşan işlenmemiş bir özel durum için bir özel durum atılır. Kaynak kodunda açıkça tanımlanmayan örtük statik oluşturucular için sorun giderme, ara dil (IL) kodunun denetlenmesi gerektirebilir.

- Statik bir oluşturucunun varlığı tür özniteliğinin eklenmesini <xref:System.Reflection.TypeAttributes.BeforeFieldInit> engeller. Bu, çalışma zamanı optimizasyonunu sınırlar.

- Beyan `static readonly` edilen bir alan yalnızca bildiriminin bir parçası olarak veya statik bir oluşturucu olarak atanabilir. Açık statik bir oluşturucu gerekli olmadığında, daha iyi çalışma zamanı optimizasyonu için statik bir oluşturucu aracılığıyla değil, bildirimde statik alanları başlaşın.

> [!Note]
> Doğrudan erişilebilir olmasa da, sorun giderme başlatma özel durumlarına yardımcı olmak için açık statik bir oluşturucunun varlığı belgelenmelidir.

### <a name="usage"></a>Kullanım

- Statik oluşturucuların tipik bir kullanımı, sınıfın bir günlük dosyası kullanması ve oluşturucunun bu dosyaya giriş yazmak için kullanılmasıdır.  
- Statik oluşturucular, yönetilmeyen kod için sarıcı sınıfları oluştururken, `LoadLibrary` oluşturucu yöntemi çağırabildiği zaman da yararlıdır.  

- Statik oluşturucular, kısıtlamalar (Tür parametre kısıtlamaları) aracılığıyla derleme zamanında denetlenemeyen tür parametresi üzerinde çalışma zamanı denetimleri uygulamak için de kullanışlı bir yerdir.

## <a name="example"></a>Örnek
 Bu örnekte, `Bus` sınıfın statik bir oluşturucusu vardır. İlk örneği `Bus` oluşturulduğunda (`bus1`), statik oluşturucu sınıfı başlatmaya çağrılır. Örnek çıktı, statik oluşturucunun iki örnek `Bus` oluşturulsa bile yalnızca bir kez çalıştığını ve örnek oluşturucu çalıştırmadan önce çalıştığını doğrular.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a>C# dili belirtimi
Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Oluşturucular](./constructors.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](./static-classes-and-static-class-members.md)
- [Sonlandırıcılar](./destructors.md)
- [Yapıcı Tasarım Yönergeleri](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Güvenlik Uyarısı - CA2121: Statik yapıcılar özel olmalıdır](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
