---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: yordam oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Yordam Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: bca5ad24e845600642429273f6053787dd290b88
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472546"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Nasıl yapılır: Yordam Oluşturma (Visual Basic)

Bir yöntemi başlangıç bildirimi ifadesiyle ( `Sub` veya `Function` ) ve bir bitiş bildirimi ifadesiyle ( `End Sub` veya) çevreedersiniz `End Function` . Tüm yordamın kodu bu deyimler arasında yer alır.

 Yordam başka bir yordam içeremez, bu nedenle başlangıç ve bitiş deyimleri başka bir yordamın dışında olmalıdır.

 Farklı yerlerde aynı görevi gerçekleştiren bir kodunuz varsa, görevi bir kez yordam olarak yazabilir ve ardından kodunuzda farklı yerlerden çağırabilirsiniz.

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Değer döndürmeyen bir yordam oluşturmak için

1. Diğer herhangi bir yordamın dışında, bir ifadesini ve `Sub` ardından bir `End Sub` ifadesini kullanın.

2. İfadesinde, `Sub` `Sub` yordam adı ile anahtar sözcüğü, sonra parantez içindeki parametre listesini izleyin.

3. Yordamın kod deyimlerini `Sub` ve deyimlerini arasına yerleştirin `End Sub` .

### <a name="to-create-a-procedure-that-returns-a-value"></a>Bir değer döndüren bir yordam oluşturmak için

1. Diğer herhangi bir yordamın dışında, bir ifadesini ve `Function` ardından bir `End Function` ifadesini kullanın.

2. İfadesinde, `Function` `Function` yordamın adı, sonra parantez içindeki parametre listesi ve `As` dönüş değerinin veri türünü belirten yan tümce ile anahtar sözcüğünü izleyin.

3. Yordamın kod deyimlerini `Function` ve deyimlerini arasına yerleştirin `End Function` .

4. `Return`Çağırma koduna değeri döndürmek için bir ifade kullanın.

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Yeni yordamınıza eski ve yinelenen kod bloklarıyla bağlanmak için

1. Yeni yordamı, eski kodun ona erişimi olan bir yerde tanımladığınızdan emin olun.

2. Eski, yinelenen kod bloğunda, yinelenen görevi gerçekleştiren deyimleri veya yordamı çağıran tek bir deyim ile değiştirin `Sub` `Function` .

3. Yordamınız bir değer döndürürse bir ise, `Function` çağırma deyiminizin döndürülen değeri olan bir eylem gerçekleştirdiğinden, örneğin bir değişkende depolanması, aksi takdirde değerin kaybedildiğinden emin olun.

## <a name="example"></a>Örnek

 Aşağıdaki `Function` yordam, iki kenarı için değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar:

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](index.md)
- [Alt Yordamlar](sub-procedures.md)
- [İşlev Yordamları](function-procedures.md)
- [Özellik Yordamları](property-procedures.md)
- [İşleç Yordamları](operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](procedure-parameters-and-arguments.md)
- [Özyinelemeli Yordamlar](recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](procedure-overloading.md)
- [Nesneler ve sınıflar](../objects-and-classes/index.md)
- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
