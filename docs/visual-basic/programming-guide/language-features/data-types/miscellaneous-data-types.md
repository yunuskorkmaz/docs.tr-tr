---
title: Çeşitli Veri Türleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 4808d87322d5b21b70ec38e2eb31b2b204938745
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821771"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Çeşitli Veri Türleri (Visual Basic)
Visual Basic, sayı veya karakterlerden doğru yönlendirilmiş olmayan çeşitli veri türleri sağlar. Bunun yerine, bunlar özelleştirilmiş verilerle gibi Evet/Hayır değerleri, tarih/saat değerleri ve nesne adresleri ilgilenir.  
  
 Visual Basic veri türleri yan yana karşılaştırmasını gösteren bir tablo için bkz: [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Boole türü  
 [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) olarak yorumlanır işaretsiz bir değer `True` veya `False`. Veri genişliği uygulama platformuna bağlıdır. Bir değişken true/false gibi yalnızca iki durumlu değerler içerebilir, Evet/Hayır veya açık/kapalı olarak bildirin `Boolean`.  
  
## <a name="date-type"></a>Tarih türü  
 [Date veri türü](../../../../visual-basic/language-reference/data-types/date-data-type.md) tarih ve saat bilgilerini tutan bir 64-bit değeri. Her 100 nanosaniyelik geçen süre (12:00 AM) başından bu yana Gregoryen takvim yılının 1 Ocak 1, temsil eder. Bir değişkenin bir tarih değeri, bir saat değeri veya her ikisini içerebilir, olarak bildirin `Date`.  
  
## <a name="object-type"></a>Nesne türü  
 [Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) uygulamanızda veya başka bir uygulama bir nesne örneğine işaret eden bir 32-bit adresidir. Bir `Object` uygulamanızın tanıdığı herhangi bir nesne veya herhangi bir veri türünde değişken başvurabilir. Her ikisi de buna dahildir *değer türleri*, gibi `Integer`, `Boolean`ve yapısı örnekleri ve *başvuru türleri*, sınıflardan gibi oluşturulan nesne örnekleriolan`String`ve <xref:System.Windows.Forms.Form>ve dizi örnekleri.  
  
 Bir değişken derleme zamanında bilmiyorsanız bir sınıfın bir örneğine bir işaretçi depolar veya verileri çeşitli veri türlerini gösterebilir, olarak bildirin `Object`.  
  
 Avantajı `Object` veri türüdür, bunu herhangi bir veri türü, verileri depolamak için kullanabileceğiniz. Olumsuz yönüyse yürütme daha uzun sürer ve uygulamanızın daha yavaş gerçekleştirmek ek işlemler tabi olur. Kullanıyorsanız bir `Object` değer türleri için değişken ücretler *kutulama* ve *kutudan çıkarma*. Başvuru türleri için kullanıyorsanız ücretler *geç bağlama*.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Sayısal Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Karakter Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Erken ve Geç Bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
