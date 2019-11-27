---
title: 'Nasıl yapılır: Yordam Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: a831814c18f97991fca8067f1c9c8e491da1b665
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344904"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Nasıl yapılır: Yordam Oluşturma (Visual Basic)

Bir başlangıç bildirimi bildirimi (`Sub` veya `Function`) ve bir bitiş bildirimi bildirimi (`End Sub` ya da `End Function`) arasında bir yordam alırsınız. Tüm yordamın kodu bu deyimler arasında yer alır.

 Yordam başka bir yordam içeremez, bu nedenle başlangıç ve bitiş deyimleri başka bir yordamın dışında olmalıdır.

 Farklı yerlerde aynı görevi gerçekleştiren bir kodunuz varsa, görevi bir kez yordam olarak yazabilir ve ardından kodunuzda farklı yerlerden çağırabilirsiniz.

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Değer döndürmeyen bir yordam oluşturmak için

1. Diğer herhangi bir yordamın dışında, bir `Sub` ifadesini ve ardından bir `End Sub` bildirisini kullanın.

2. `Sub` bildiriminde, yordamın adı ile `Sub` anahtar sözcüğünü, sonra da parantez içindeki parametre listesini izleyin.

3. Yordamın kod deyimlerini `Sub` ve `End Sub` deyimleri arasına yerleştirin.

### <a name="to-create-a-procedure-that-returns-a-value"></a>Bir değer döndüren bir yordam oluşturmak için

1. Diğer herhangi bir yordamın dışında, bir `Function` ifadesini ve ardından bir `End Function` bildirisini kullanın.

2. `Function` bildiriminde, yordamın adı, sonra parantez içindeki parametre listesi ve dönüş değerinin veri türünü belirten bir `As` yan tümcesi ile `Function` anahtar sözcüğünü izleyin.

3. Yordamın kod deyimlerini `Function` ve `End Function` deyimleri arasına yerleştirin.

4. Değeri çağırma koduna döndürmek için bir `Return` ifadesini kullanın.

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Yeni yordamınıza eski ve yinelenen kod bloklarıyla bağlanmak için

1. Yeni yordamı, eski kodun ona erişimi olan bir yerde tanımladığınızdan emin olun.

2. Eski, yinelenen kod bloğunda, yinelenen görevi gerçekleştiren deyimleri `Sub` veya `Function` yordamını çağıran tek bir deyim ile değiştirin.

3. Yordamınız bir değer döndüren bir `Function` ise, çağırma deyiminizin döndürülen değeri olan bir eylem gerçekleştirdiğinden emin olun (örneğin, bir değişkende depolanması) veya aksi takdirde değer kaybedilir.

## <a name="example"></a>Örnek

 Aşağıdaki `Function` yordam, iki tarafa ait değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar:

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
