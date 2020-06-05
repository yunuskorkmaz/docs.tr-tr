---
title: Çeşitli Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 0a08c0e7087c3efb0e5ffce51182defae45629ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393759"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Çeşitli Veri Türleri (Visual Basic)
Visual Basic, sayı veya karakterlere yönelik olmayan çeşitli veri türleri sağlar. Bunun yerine, Evet/Hayır değerleri, tarih/saat değerleri ve nesne adresleri gibi özelleşmiş verilerle ilgilenir.  
  
 Visual Basic veri türlerinin yan yana karşılaştırmasını gösteren bir tablo için bkz. [veri türleri](../../../language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Boole türü  
 [Boolean veri türü](../../../language-reference/data-types/boolean-data-type.md) veya olarak yorumlanan işaretsiz bir değerdir `True` `False` . Veri genişliği, uygulama platformuna bağlıdır. Bir değişken yalnızca doğru/yanlış, Evet/Hayır veya açık/kapalı gibi yalnızca iki durumlu değerler içeriyorsa, olarak bildirin `Boolean` .  
  
## <a name="date-type"></a>Tarih türü  
 [Tarih veri türü](../../../language-reference/data-types/date-data-type.md) , hem tarih hem de saat bilgilerini tutan 64 bitlik bir değerdir. Her artış, Gregoryen takvimdeki 1 Ocak 100 ' den (12:00) itibaren geçen sürenin nanosaniye süresini temsil eder. Bir değişken bir tarih değeri, saat değeri veya her ikisi de içeriyorsa, olarak bildirin `Date` .  
  
## <a name="object-type"></a>Nesne Türü  
 [Nesne veri türü](../../../language-reference/data-types/object-data-type.md) , uygulamanızdaki bir nesne örneğine veya başka bir uygulamaya işaret eden 32 bitlik bir adrestir. Bir `Object` değişken, uygulamanızın tanıdığı herhangi bir nesneye veya herhangi bir veri türünün verilerine başvurabilir. Bu,, ve yapı örnekleri gibi *değer türlerini*ve, ve `Integer` `Boolean` dizi örnekleri gibi sınıflardan oluşturulan nesne örnekleri olan *başvuru türlerini*içerir `String` <xref:System.Windows.Forms.Form> .  
  
 Bir değişken, derleme zamanında tanımadığınız bir sınıfın örneğine bir işaretçi depolarsa veya çeşitli veri türlerindeki verileri işaret edebilir, olarak bildirin `Object` .  
  
 Veri türünün avantajı, `Object` herhangi bir veri türünün verilerini depolamak için kullanabilirsiniz. Dezavantajı, daha fazla yürütme süresi alan ve uygulamanızı daha yavaş hale getirebilmeniz için ek işlemlere neden olur. `Object`Değer türleri için bir değişken kullanırsanız, *kutulama* ve *kutudan*çıkarma uygulanır. Bunu başvuru türleri için kullanıyorsanız, *geç bağlamaya*tabi olursunuz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Karakterleri](type-characters.md)
- [Başlangıç Veri Türleri](elementary-data-types.md)
- [Sayısal Veri Türleri](numeric-data-types.md)
- [Karakter Veri Türleri](character-data-types.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Erken ve geç bağlama](../early-late-binding/index.md)
