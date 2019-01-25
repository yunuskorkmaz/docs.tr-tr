---
title: Yerel işlevler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e91069c25ebe6c2a22927391734e5030a908e4ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663933"
---
# <a name="local-functions-c-programming-guide"></a>Yerel işlevler (C# programlama Kılavuzu)

C# 7.0, C# destekleyen'ile başlayan *yerel işlevler*. Yerel işlevler başka bir üye iç içe geçmiş özel bir tür yöntemlerdir. Bunlar, yalnızca kendi kapsayan üyeden çağrılabilir. Yerel işlevler içinde bildirilen ve çağrılır:

- Yöntemler, özellikle Yineleyici ve zaman uyumsuz yöntemleri
- Oluşturucular
- Özellik erişimcileri
- Olay erişimcileri
- Anonim yöntemler
- Lambda ifadeleri
- Sonlandırıcılar
- Diğer yerel işlevler

Ancak, yerel işlevler bir ifade gövdeli üyenin içinde bildirilemez.

> [!NOTE]
> Bazı durumlarda, bir lambda ifadesi, ayrıca yerel bir işlev tarafından desteklenen işlevselliği uygulamak için kullanabilirsiniz. Bir karşılaştırması için bkz. [Lambda ifadeleri karşılaştırma yerel işlevler](../../local-functions-vs-lambdas.md).

Yerel işlevler Temizle, kodun amacı olun. Herkes okuma, kod yöntemi içeren yöntemi tarafından çağrılabilir dışında olduğunu görebilirsiniz. Takım projeleri için bunlar da yanlışlıkla doğrudan yerlerden yöntemini çağırmak başka bir geliştirici imkansız hale sınıf veya yapı içinde.
 
## <a name="local-function-syntax"></a>Yerel işlev sözdizimi

Yerel bir işlev içeren bir üye iç içe geçmiş bir yöntemde olarak tanımlanır. Tanımı sözdizimi aşağıdaki gibidir:

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Yerel işlevler kullanabileceğiniz [zaman uyumsuz](../../language-reference/keywords/async.md) ve [güvenli](../../language-reference/keywords/unsafe.md) değiştiriciler. 

Yöntem parametreleri içeren üyesinde tanımlanan tüm yerel değişkenlerin yerel işlevde erişilebilir olduğunu unutmayın. 

Bir yöntem tanımını bir yerel işlev tanımı aşağıdaki öğeleri içeremez:

- Üye erişim değiştiricisi. Tüm yerel işlevler özel olduğundan, bir erişim değiştiricisidir gibi `private` anahtar sözcüğü, Derleyici Hatası CS0106, "'private' değiştiricisi bu öğe için geçerli değil." oluşturur
 
- [Statik](../../language-reference/keywords/static.md) anahtar sözcüğü. Dahil olmak üzere `static` anahtar sözcüğü, Derleyici Hatası CS0106 oluşturur, "'static' değiştiricisi bu öğe için geçerli değil."

Ayrıca, öznitelikler, yerel bir işlev veya parametrelerini uygulanamaz ve tür parametreleri. 
 
Aşağıdaki örnek adlı bir yerel işlev tanımlar `AppendPathSeparator` adlı bir yöntem özel olan `GetText`:
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Yerel işlevler ve özel durumlar

Yerel işlevler yararlı özelliklerini hemen yüzey özel durumlara izin verebilirsiniz biridir. Yöntemi yineleyiciler için özel durumlar döndürülen dizi yalnızca numaralandırılana zaman ve yineleyici alınamaz zaman takip edilir. Döndürülen görevin bekletildiğinde zaman uyumsuz yöntemler için zaman uyumsuz bir yöntem içinde oluşturulan özel durumlar gözlenmiştir. 

Aşağıdaki örnekte tanımlayan bir `OddSequence` tek sayıları belirtilen bir aralıktaki arasında numaralandırır yöntemi. Bir sayı için 100'den büyük geçirdiği için `OddSequence` Numaralandırıcı yöntemi çağırılıyorsa yöntem bir <xref:System.ArgumentOutOfRangeException>. Örneğin çıktısında gösterildiği gibi özel durum sayıları yalnızca yineleme yapmak ve Numaralandırıcı alamaz zamanı ortaya çıkarır.

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Bunun yerine, doğrulama yapılırken bir özel durum oluşturabilecek ve yerel bir işlevden yineleyici döndürerek yineleyici almadan önce aşağıdaki örnekte görüldüğü gibi.

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Yerel İşlevler, zaman uyumsuz işlemi dışında özel durumları işlemek için benzer bir şekilde kullanılabilir. Normalde, zaman uyumsuz yöntemde oluşan özel durum iç özel durumları incelemeniz gerektiren bir <xref:System.AggregateException>. Yerel işlevler hızlı başarısız olma ve özel durum hem zaman uyumlu olarak gözlemlenen izin vermek kodunuzu izin verir.

Aşağıdaki örnekte adlı bir zaman uyumsuz yöntem `GetMultipleAsync` belirtilen sayıda saniye için Duraklat ve o saniye sayısını rastgele katları olan bir değer döndürür. En büyük gecikme değeri 5 saniyedir; bir <xref:System.ArgumentOutOfRangeException> değer 5'ten büyük olduğunda oluşur. Aşağıdaki örnekte gösterildiği gibi 6 değeri olduğunda oluşturulan özel durum geçirilen `GetMultipleAsync` yöntemi içinde kaydırılır bir <xref:System.AggregateException> sonra `GetMultipleAsync` yöntemi yürütülmesine başlar.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

İle yöntemi yineleyici yaptığımız gibi Biz bu örnekte, zaman uyumsuz yöntemi çağırmadan önce doğrulamayı gerçekleştirmek için kodu yeniden düzenleyebilirsiniz. Aşağıdaki örnekte gösterildiği çıktısı olarak <xref:System.ArgumentOutOfRangeException> , sarmalanmamış bir <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Ayrıca bkz.

- [Yöntemler](methods.md)
