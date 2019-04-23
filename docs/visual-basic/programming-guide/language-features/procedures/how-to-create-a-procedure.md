---
title: 'Nasıl yapılır: Bir yordam (Visual Basic) oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 56099d334a03e85b816cf48983cbbead0784ef5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320398"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Nasıl yapılır: Bir yordam (Visual Basic) oluşturma
Bir yordamın başlangıç bir bildirim deyiminin arasında alın (`Sub` veya `Function`) hem de bitiş bildirimi deyimi (`End Sub` veya `End Function`). Bu deyimler tüm yordam kodu arasındadır.  
  
 Kendi başlangıç ve bitiş deyimleri dışında herhangi bir yordam olması gerekir başka bir yordama yordam içeremez.  
  
 Farklı yerlerde aynı görevi gerçekleştiren bir kod varsa, bir yordam görevi bir kez yazın ve ardından kodunuzda farklı yerden çağırın.  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Bir değer döndürmeyen bir yordam oluşturmak için  
  
1. Diğer herhangi bir yordam dışında kullanmak bir `Sub` deyimi, arkasından bir `End Sub` deyimi.  
  
2. İçinde `Sub` deyimi izleyin `Sub` yordamı sonra parantez parametre listesinde adıyla anahtar sözcüğü.  
  
3. Yordam kod deyimlerini arasında yerleştirin `Sub` ve `End Sub` deyimleri.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Bir değer döndüren bir yordam oluşturmak için  
  
1. Diğer herhangi bir yordam dışında kullanmak bir `Function` deyimi, arkasından bir `End Function` deyimi.  
  
2. İçinde `Function` deyimi izleyin `Function` yordamı sonra parantez, parametre listesinde adıyla anahtar sözcüğü ve ardından bir `As` dönüş değeri veri türünü belirleme yan tümcesi.  
  
3. Yordam kod deyimlerini arasında yerleştirin `Function` ve `End Function` deyimleri.  
  
4. Kullanım bir `Return` deyimini çağrıldığı koda bir değer döndürür.  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Yeni bir yordam kodu eski, yinelenen blok ile bağlanmak için  
  
1. Eski kod erişimi sahip olduğu bir yerde yeni bir yordam tanımlamak emin olun.  
  
2. Çağıran tek bir deyim ile yinelenen görevi gerçekleştirmek için ifadeleri, eski ve yinelenen bir kod bloğunda değiştirin `Sub` veya `Function` yordamı.  
  
3. Yordamınız ise bir `Function` bir değer döndüren, çağıran Ekstrenizi bir değişkende depolanması gibi döndürülen değerle bir eylem gerçekleştirir; Aksi takdirde, değeri kaybolur emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki `Function` yordamı, en uzun kenar veya, diğer iki yüz için değerlerine dik üçgenin, hipotenüsü hesaplar.  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Özyinelemeli Yordamlar](./recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
