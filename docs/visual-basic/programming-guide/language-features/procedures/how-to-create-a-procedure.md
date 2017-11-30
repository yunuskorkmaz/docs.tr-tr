---
title: "Nasıl yapılır: Yordam Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a44918b7a1426d215cee0ff2981f5763432a48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Nasıl yapılır: Yordam Oluşturma (Visual Basic)
Bir başlangıç bildirimi deyimi arasında bir yordam alın (`Sub` veya `Function`) hem de bitiş bildirimi deyimi (`End Sub` veya `End Function`). Tüm yordamın kodu arasında bu deyimleri arasındadır.  
  
 Başlangıç ve bitiş deyimleri dışında herhangi bir yordam olmalıdır bir yordam başka bir yordam içeremez.  
  
 Farklı yerlerde aynı görevi gerçekleştiren kodu varsa, görev bir yordam olarak bir kez yazma ve daha sonra kodunuzda farklı yerlerden çağırın.  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Bir değer döndürmeyen bir yordam oluşturmak için  
  
1.  Diğer herhangi bir yordam dışında kullanmak bir `Sub` deyimi, arkasından bir `End Sub` deyimi.  
  
2.  İçinde `Sub` deyimi, izleyin `Sub` yordamı sonra parantez içinde parametre listesi adı olan anahtar sözcük.  
  
3.  Yordam kod deyimleri arasında yerleştirin `Sub` ve `End Sub` deyimleri.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Bir değer döndüren bir yordam oluşturmak için  
  
1.  Diğer herhangi bir yordam dışında kullanmak bir `Function` deyimi, arkasından bir `End Function` deyimi.  
  
2.  İçinde `Function` deyimi, izleyin `Function` yordamı, ardından parantez parametre listesinde adıyla anahtar sözcüğü ve ardından bir `As` dönüş değeri veri türünü belirten yan tümcesi.  
  
3.  Yordam kod deyimleri arasında yerleştirin `Function` ve `End Function` deyimleri.  
  
4.  Kullanım bir `Return` deyimi çağıran kodu değerini döndürür.  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Yeni yordamınız kodu eski, yinelenen blok ile bağlanmak için  
  
1.  Eski kod erişime sahip olduğu bir yerde yeni bir yordam tanımlamak emin olun.  
  
2.  Çağıran tek bir deyimde olan yinelenen görev gerçekleştirmek deyimleri, eski, yinelenen kod bloğunda Değiştir `Sub` veya `Function` yordamı.  
  
3.  Yordamınız ise bir `Function` bir değer döndüren, çağıran deyiminizde bir değişkende saklamak gibi döndürülen değer, bir eylem gerçekleştirir Aksi takdirde değer kaybolacak emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki `Function` yordamı en uzun taraf veya diğer iki kenara için değerlerine göre bir sağ üçgen hipotenüsü hesaplar.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Alt yordamlar](./sub-procedures.md)  
 [İşlev yordamları](./function-procedures.md)  
 [Özellik yordamları](./property-procedures.md)  
 [İşleç yordamları](./operator-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Özyinelemeli yordamlar](./recursive-procedures.md)  
 [Yordam aşırı yüklemesi](./procedure-overloading.md)  
 [Nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Nesne odaklı programlama](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
