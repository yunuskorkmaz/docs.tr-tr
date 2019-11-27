---
title: Çeşitli Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: cc6262b5bb305bb839917e222d831fa3340a1b14
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346343"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Çeşitli Veri Türleri (Visual Basic)
Visual Basic, sayı veya karakterlere yönelik olmayan çeşitli veri türleri sağlar. Bunun yerine, Evet/Hayır değerleri, tarih/saat değerleri ve nesne adresleri gibi özelleşmiş verilerle ilgilenir.  
  
 Visual Basic veri türlerinin yan yana karşılaştırmasını gösteren bir tablo için bkz. [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Boole türü  
 [Boolean veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) , `True` veya `False`olarak yorumlanan işaretsiz bir değerdir. Veri genişliği, uygulama platformuna bağlıdır. Bir değişken yalnızca doğru/yanlış, Evet/Hayır veya açık/kapalı gibi yalnızca iki durumlu değerler içeriyorsa, bunu `Boolean`olarak bildirin.  
  
## <a name="date-type"></a>Tarih türü  
 [Tarih veri türü](../../../../visual-basic/language-reference/data-types/date-data-type.md) , hem tarih hem de saat bilgilerini tutan 64 bitlik bir değerdir. Her artış, Gregoryen takvimdeki 1 Ocak 100 ' den (12:00) itibaren geçen sürenin nanosaniye süresini temsil eder. Bir değişken bir tarih değeri, saat değeri veya her ikisi de içeriyorsa, `Date`olarak bildirin.  
  
## <a name="object-type"></a>Nesne Türü  
 [Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) , uygulamanızdaki bir nesne örneğine veya başka bir uygulamaya işaret eden 32 bitlik bir adrestir. `Object` bir değişken, uygulamanızın tanıdığı herhangi bir nesneye veya herhangi bir veri türüne ait verilere başvurabilir. Bu, `Integer`, `Boolean`ve yapı örnekleri gibi *değer türlerini*ve `String` ve <xref:System.Windows.Forms.Form>ve dizi örnekleri gibi sınıflardan oluşturulan nesne örnekleri olan *başvuru türlerini*içerir.  
  
 Bir değişken, derleme zamanında tanımadığınız bir sınıfın örneğine bir işaretçi depolarsa veya çeşitli veri türlerindeki verileri işaret edebilir, `Object`olarak bildirin.  
  
 `Object` veri türünün avantajı, herhangi bir veri türünün verilerini depolamak için bunu kullanmanıza olanak sağlar. Dezavantajı, daha fazla yürütme süresi alan ve uygulamanızı daha yavaş hale getirebilmeniz için ek işlemlere neden olur. Değer türleri için bir `Object` değişkeni kullanırsanız *kutulama* ve *kutudan*çıkarma uygulanır. Bunu başvuru türleri için kullanıyorsanız, *geç bağlamaya*tabi olursunuz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Sayısal Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Karakter Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Erken ve Geç Bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
