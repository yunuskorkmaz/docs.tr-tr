---
title: 'Nasıl yapılır: Yordam oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 2cf4c788ec421c1e74ef7198496a92149e049752
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216726"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Nasıl yapılır: Yordam oluşturma (Visual Basic)

Bir yöntemi başlangıç bildirimi ifadesiyle`Sub` (veya `Function`) ve bir bitiş bildirimi ifadesiyle (`End Sub` veya `End Function`) çevreedersiniz. Tüm yordamın kodu bu deyimler arasında yer alır.

 Yordam başka bir yordam içeremez, bu nedenle başlangıç ve bitiş deyimleri başka bir yordamın dışında olmalıdır.

 Farklı yerlerde aynı görevi gerçekleştiren bir kodunuz varsa, görevi bir kez yordam olarak yazabilir ve ardından kodunuzda farklı yerlerden çağırabilirsiniz.

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Değer döndürmeyen bir yordam oluşturmak için

1. Diğer herhangi bir yordamın dışında, bir `Sub` ifadesini ve ardından `End Sub` bir ifadesini kullanın.

2. İfadesinde, yordam adı ile `Sub` anahtar sözcüğü, sonra parantez içindeki parametre listesini izleyin. `Sub`

3. Yordamın kod deyimlerini `Sub` ve `End Sub` deyimlerini arasına yerleştirin.

### <a name="to-create-a-procedure-that-returns-a-value"></a>Bir değer döndüren bir yordam oluşturmak için

1. Diğer herhangi bir yordamın dışında, bir `Function` ifadesini ve ardından `End Function` bir ifadesini kullanın.

2. İfadesinde, yordamın adı, sonra `Function` `As` parantez içindeki parametre listesi ve dönüş değerinin veri türünü belirten yan tümce ile anahtar sözcüğünü izleyin. `Function`

3. Yordamın kod deyimlerini `Function` ve `End Function` deyimlerini arasına yerleştirin.

4. Çağırma koduna `Return` değeri döndürmek için bir ifade kullanın.

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Yeni yordamınıza eski ve yinelenen kod bloklarıyla bağlanmak için

1. Yeni yordamı, eski kodun ona erişimi olan bir yerde tanımladığınızdan emin olun.

2. Eski, yinelenen kod bloğunda, yinelenen görevi gerçekleştiren deyimleri `Sub` veya `Function` yordamı çağıran tek bir deyim ile değiştirin.

3. Yordamınız bir değer döndürürse `Function` bir ise, çağırma deyiminizin döndürülen değeri olan bir eylem gerçekleştirdiğinden, örneğin bir değişkende depolanması, aksi takdirde değerin kaybedildiğinden emin olun.

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
- [Nesneler ve Sınıflar](../objects-and-classes/index.md)
- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
