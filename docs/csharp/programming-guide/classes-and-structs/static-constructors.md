---
title: Statik oluşturucular - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 9cf977be84a4d3098e009d5a58d0c12ad2000e92
ms.sourcegitcommit: ced0cccf15adfd492f8196cb739f01dde52c9252
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67135643"
---
# <a name="static-constructors-c-programming-guide"></a>Statik Oluşturucular (C# Programlama Kılavuzu)
Statik Oluşturucu herhangi başlatmak için kullanılan [statik](../../../csharp/language-reference/keywords/static.md) verileri veya yalnızca bir kez gerçekleştirilmesi gereken belirli bir eylemi gerçekleştirmek için. İlk örneği oluşturulduğunda veya herhangi bir statik üye başvurulan önce otomatik olarak adlandırılır.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
 
## <a name="remarks"></a>Açıklamalar
Statik Oluşturucular, aşağıdaki özelliklere sahiptir:  
  
- Statik Oluşturucu erişim değiştiricileri alın veya parametreleri desteklemez.  

- Bir sınıf veya yapı, yalnızca bir statik Oluşturucu olabilir.

- Statik oluşturucular devralınmış veya aşırı yüklenmiş.

- Statik Oluşturucu yalnızca ortak dil çalışma (CLR) tarafından çağrılacak tutulmamıştır ve doğrudan çağrılamaz. Otomatik olarak çağrılır.

- Kullanıcının statik Oluşturucu programa ne zaman çalıştırılır üzerinde denetimi yoktur.
  
- Statik Oluşturucu otomatik olarak başlatmak için çağırılır [sınıfı](../../../csharp/language-reference/keywords/class.md) önce ilk örneği oluşturulduğunda veya herhangi bir statik üye başvurulur. Statik Oluşturucu bir örnek oluşturucusu önce çalıştırılır. Bir türün statik Oluşturucusu bir olay ya da temsilci atanmış statik bir yöntemi çağrıldığında ve değil atandığı zaman çağrıldığını unutmayın. Statik alan değişken başlatıcıları statik oluşturucunun sınıfında mevcut olması durumunda, statik oluşturucunun yürütülmeden hemen önce sınıf bildiriminde göründükleri metinsel sırayla yürütülür.

- Statik alanları başlatmak için bir statik Oluşturucu sağlamazsanız, tüm statik alanları varsayılan değerlerine bağlantısında listelendiği gibi başlatılır [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). 
  
- Statik Oluşturucu bir özel durum oluşturursa, çalışma zamanı, ikinci kez çağırmayacaktır ve türü, programınızın çalıştığı uygulama etki alanı ömrü boyunca başlatılmamış kalır. En yaygın olarak, bir <xref:System.TypeInitializationException> statik Oluşturucu bir tür örneği işlenemediğinde özel durum ya da statik oluşturucu içinde bir işlenmeyen özel durum ortaya çıkma için. Kaynak kodunda açıkça tanımlanmayan örtük statik oluşturucular için sorun giderme Ara dil (IL) kod İnceleme gerektirebilir.

- Statik Oluşturucu varlığını eklenmesini engeller <xref:System.Reflection.TypeAttributes.BeforeFieldInit> tür özniteliği. Bu, çalışma zamanı iyileştirmesi sınırlar.

- Bir alan olarak bildirilen `static readonly` yalnızca bildiriminden veya bir statik oluşturucunun parçası olarak atanabilir. Açık bir statik Oluşturucu gerekli olmadığı durumlarda, daha iyi çalışma zamanı iyileştirmesi için statik bir oluşturucu üzerinden değil, bildirim sırasında statik alanları başlatın.

> [!Note]
> Doğrudan erişilemez ancak başlatma özel durum sorunlarını giderme ile yardımcı olmak için açık bir statik Oluşturucu varlığını belgelenmelidir.

### <a name="usage"></a>Kullanım

- Tipik bir kullanımı statik Oluşturucular, sınıf, bir günlük dosyası kullanarak ve oluşturucu girişleri bu dosyaya yazmak için kullanılan andır.  
- Statik oluşturucular da yararlı Oluşturucu çağırabilir, yönetilmeyen kod için sarmalayıcı sınıflar oluşturma `LoadLibrary` yöntemi.  

- Statik oluşturucular ayrıca iade edilemez kısıtlamaları (tür parametresi kısıtlamaları) aracılığıyla derleme zamanında tür parametresi üzerinde çalışma zamanı denetimleri zorunlu kılmak için uygun bir yer var.

## <a name="example"></a>Örnek
 Bu örnekte, sınıf `Bus` bir statik Oluşturucusu vardır. Zaman ilk örneğinin `Bus` oluşturulur (`bus1`), sınıf için statik Oluşturucu çağrılır. Statik Oluşturucu yalnızca bir kez olsa bile iki örneği çalıştığından örnek çıktısı doğrular `Bus` oluşturulur, ve örnek oluşturucu döngülerinden önce çalışır.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]
 
## <a name="c-language-specification"></a>C# dili belirtimi
Daha fazla bilgi için [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [Oluşturucu tasarımı yönergeleri](../../../docs/standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Güvenlik Uyarısı - CA2121: Statik oluşturucular özel olmalıdır](https://docs.microsoft.com/en-us/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
