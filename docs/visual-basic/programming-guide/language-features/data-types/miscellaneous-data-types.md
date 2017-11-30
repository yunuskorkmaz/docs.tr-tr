---
title: "Çeşitli Veri Türleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6bb86bb6d203aa4e6bdded27a4cb78a8155ddec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="miscellaneous-data-types-visual-basic"></a>Çeşitli Veri Türleri (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]rakam veya karakter doğru odaklı olmayan birkaç veri türlerini sağlar. Bunun yerine, bunlar özel verilerle gibi Evet/Hayır değerleri, tarih/saat değerleri ve nesne adresleri ilgilenir.  
  
 Yan yana karşılaştırmasını gösteren bir tablo için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türlerini görmek [veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="boolean-type"></a>Boolean türü  
 [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) olarak yorumlanır imzasız bir değer `True` veya `False`. Veri genişliği uygulama platformuna bağlıdır. Bir değişken true/false gibi yalnızca iki durumlu değerler içerebilir, Evet/Hayır, veya açık/kapalı olarak bildirme `Boolean`.  
  
## <a name="date-type"></a>Tarih türü  
 [Tarih veri türü](../../../../visual-basic/language-reference/data-types/date-data-type.md) tarih ve saat bilgilerini tutan bir 64-bit değeridir. Her artış 100 nanosaniye geçen süre (12:00 AM) başına itibaren Gregoryen takvim 1 yılının 1 Ocak, temsil eder. Bir değişkenin bir tarih değeri, bir saat değeri veya her ikisini içerebilir, olarak bildirme `Date`.  
  
## <a name="object-type"></a>Nesne türü  
 [Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) noktalarını bir nesne örneği, uygulamanızda veya başka bir uygulama için bir 32 bit adresidir. Bir `Object` değişkeni uygulamanızın tanıdığı herhangi bir nesne ya da herhangi bir veri türünde başvurabilir. Bu, her ikisi de içerir *değer türleri*, gibi `Integer`, `Boolean`ve yapısı örnekleri ve *başvuru türleri*, sınıflardan gibi oluşturulan nesneler örnekleriolan`String`ve <xref:System.Windows.Forms.Form>ve dizi örnekleri.  
  
 Derleme zamanında bilmiyorsanız sınıfının bir örneği için bir işaretçi bir değişkeni depolar veya çeşitli veri türlerinin veri gösterebilir, olarak bildirme `Object`.  
  
 Avantajı `Object` veri türü olan, bunu herhangi bir veri türü, verileri depolamak için kullanabileceğiniz. Olumsuz daha fazla yürütme süresi almak ve uygulamanızı daha yavaş gerçekleştirmek yapan ek işlemleri neden olur. Kullanırsanız, bir `Object` değişken değer türleri için tabi *kutulama* ve *kutudan çıkarma*. Referans türleri için kullanırsanız, tabi *geç bağlama*.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Başlangıç veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Sayısal veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Karakter veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Veri türleri sorunlarını giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Erken ve geç bağlama](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
