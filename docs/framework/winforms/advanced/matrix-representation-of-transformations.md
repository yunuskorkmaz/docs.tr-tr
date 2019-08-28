---
title: Dönüşümlerin Matrisle Temsili
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
ms.openlocfilehash: 24da407de24a924a68466e4301cc3f4a74cb2e94
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044246"
---
# <a name="matrix-representation-of-transformations"></a>Dönüşümlerin Matrisle Temsili
Bir a × n matrisi, k satırı ve n sütunu olarak düzenlenmiş bir sayı kümesidir. Aşağıdaki çizimde çeşitli matrisler gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Ayrı ayrı öğeler ekleyerek aynı boyutta iki matrisi ekleyebilirsiniz. Aşağıdaki çizimde, matris eklemenin iki örneği gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 M × n matrisi n × p matrisi ile çarpılır ve sonuç bir m × p matrisi olur. İlk matriste sütunların sayısı ikinci Matristeki satır sayısıyla aynı olmalıdır. Örneğin, 4 × 2 matrisi 4 × 3 matrisi oluşturmak için 2 × 3 matrisi ile çarpılarak belirtilebilir.  
  
 Bir matrisin düzlemin ve satır ve sütunlarındaki noktaları vektör olarak düşünülebilir. Örneğin, (2, 5) iki bileşeni olan bir vektördür ve (3, 7, 1) üç bileşeni olan bir vektördür. İki vektörün nokta ürünü aşağıdaki gibi tanımlanır:  
  
 (a, b) • (c, d) = AC + BD  
  
 (a, b, c) • (d, e, f) = ad + ve + CF  
  
 Örneğin, (2, 3) ve (5, 4) noktası ürünü, (2) (5) + (3) (4) = 22 ' dir. (2, 5, 1) ve (4, 3, 1) noktası ürünü (2) (4) + (5) (3) + (1) (1) = 24 ' tir. İki vektörün nokta ürününün başka bir vektör değil, bir sayı olduğunu unutmayın. Ayrıca, yalnızca iki Vektörün aynı sayıda bileşeni varsa, nokta ürününü hesaplayabileceğinizi unutmayın.  
  
 A (i, j), a 'nın A 'da, a 'daki ve jth sütunundaki giriş şeklinde olmasına izin verir. Örneğin, A (3, 2) 3. satırdaki ve 2. sütundaki matris A ' daki girdidir. A, B ve C 'nin matrisleri ve AB = C olduğunu varsayalım. C girdileri aşağıdaki şekilde hesaplanır:  
  
 C (i, j) = (A 'nın satır ı) • (B sütunu B)  
  
 Aşağıdaki çizimde matris çarpın birkaç örneği gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Düzlemin içindeki bir noktayı 1 × 2 matrisi olarak düşünüyorsanız, bu noktayı 2 × 2 matrisi çarparak dönüştürebilirsiniz. Aşağıdaki çizimde, noktaya (2, 1) uygulanan çeşitli dönüştürmeler gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Yukarıdaki şekilde gösterilen tüm dönüşümler doğrusal dönüşümlerdir. Çeviri gibi bazı diğer dönüşümler doğrusal değildir ve 2 × 2 matrisinde çarpma olarak ifade edilemez. (2, 1) noktasıyla başlamak, 90 derece döndürmek, 3 birimi x yönünde çevirmek ve y yönünde 4 birim çevirmek istediğinizi varsayalım. Bunu, matris bir çarpma kullanarak ve ardından matris ekleyerek gerçekleştirebilirsiniz.  
  
 ![Dönüşümler](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Doğrusal bir dönüştürme (2 × 2 matris ile çarparak) ve ardından çeviri (1 × 2 matris ekleme), bir afin dönüştürmesi olarak adlandırılır. Bir ölçü çiftinde (bir tane doğrusal bölüm ve çeviri için bir) bir Afine dönüştürmeyi depolamanın bir alternatifi, tüm dönüşümün 3 × 3 matrisi içinde depolanması olur. Bu işi yapmak için düzlemdeki bir noktanın kukla bir 3 matris ile bir 1 × 3 matrisinde depolanması gerekir. Her üç koordinat de 1 ' e eşit hale getirmek, olağan bir tekniktir. Örneğin, (2, 1) noktası [2 1 1] matrisi tarafından temsil edilir. Aşağıdaki çizimde bir Afine dönüştürme (90 derece döndür; x yönünde 3 birim çevir, y yönünde 4 birim), tek bir 3 × 3 matrisi çarpma olarak ifade edilir.  
  
 ![Dönüşümler](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 Yukarıdaki örnekte, (2, 1) noktası (2, 6) noktasına eşlendi. 3 × 3 matrisinin üçüncü sütununun 0, 0, 1 sayılarını içerdiğini unutmayın. Bu, bir afin dönüşümünün 3 × 3 matrisi için her zaman durum olacaktır. Önemli sayılar, 1 ve 2 sütunlarındaki altı sayıdır. Matrisin sol üst 2 × 2 bölümü, dönüştürmenin doğrusal parçasını temsil eder ve 3. satırdaki ilk iki giriş, çeviriyi temsil eder.  
  
 ![Dönüşümler](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 GDI+ ' da, bir <xref:System.Drawing.Drawing2D.Matrix> nesneye bir afin dönüştürmeyi saklayabilirsiniz. Bir Afine dönüştürmeyi temsil eden bir matrisin üçüncü sütunu her zaman (0, 0, 1) olduğunda, bir <xref:System.Drawing.Drawing2D.Matrix> nesne oluştururken yalnızca ilk iki sütundaki altı sayıyı belirtirsiniz. İfade `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` , yukarıdaki şekilde gösterilen matrisi oluşturur.  
  
## <a name="composite-transformations"></a>Bileşik dönüşümler  
 Bileşik dönüşüm, diğeri diğeri tarafından izlenen bir dizi dönüşümdir. Aşağıdaki listedeki matrisleri ve dönüştürmeleri göz önünde bulundurun:  
  
|||  
|-|-|  
|A matrisi|90 derece döndür|  
|Matris B|X yönünde 2 faktörüyle ölçeklendirin|  
|Matris C|Y yönünde 3 birim çevirin|  
  
 Matris [2 1 1] ile temsil edilen nokta (2, 1) ile başlıyoruz ve A, B ve ardından C ile çarpıp, bu nokta (2, 1), üç dönüştürmeyi listelenen sırayla üstlerine gidecektir.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Bileşik dönüşümün üç parçasını üç ayrı matrisde depolamak yerine, bileşik dönüşümün tamamını depolayan tek 3 × 3 matris almak için A, B ve C 'yi birlikte çarpın. ABC = D olduğunu varsayalım. Ardından D ile çarpılmış bir nokta, A, sonra B ve C ile çarpılarak aynı sonucu verir.  
  
 [2 1 1] D = [-2 5 1]  
  
 Aşağıdaki çizimde A, B, C ve D matrisleri gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Bir bileşik dönüştürme matrisinin tek tek dönüştürme matrislerini çarparak biçimlendirilmiş olması, herhangi bir tür aflik dönüşümlerinin tek <xref:System.Drawing.Drawing2D.Matrix> bir nesnede saklanabileceği anlamına gelir.  
  
> [!CAUTION]
> Bileşik dönüşüm sırası önemlidir. Genel olarak, döndürün, ardından ölçeklendirin, ardından çevir, ölçeklendirilmesi ile aynı değildir, sonra döndürün ve ardından çevirin. Benzer şekilde, matris çarpın sırası önemlidir. Genel olarak, ABC, arka arkaya aynı değildir.  
  
 <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A> <xref:System.Drawing.Drawing2D.Matrix.Translate%2A> <xref:System.Drawing.Drawing2D.Matrix.Scale%2A> <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A> <xref:System.Drawing.Drawing2D.Matrix.Shear%2A> <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>Sınıfı, bileşik dönüşüm oluşturmak için çeşitli yöntemler sağlar:,,,, ve. <xref:System.Drawing.Drawing2D.Matrix> Aşağıdaki örnek, ilk olarak 30 derece döndüren bileşik bir dönüşümün matrisini oluşturur, sonra y yönünde 2 faktörüyle ölçeklendirir ve sonra x yönünde 5 birim çevirir:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 Aşağıdaki çizimde matris gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koordinat Sistemleri ve Dönüştürmeler](coordinate-systems-and-transformations.md)
- [Yönetilen GDI+'da Dönüştürmeleri Kullanma](using-transformations-in-managed-gdi.md)
