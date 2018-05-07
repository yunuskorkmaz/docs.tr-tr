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
ms.openlocfilehash: 4c840d8a5abc89493bc684526ce76d34307f4ba1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="matrix-representation-of-transformations"></a>Dönüşümlerin Matrisle Temsili
Bir m × n matris m satır ve n sütunlarda düzenlenmiş numaraları kümesidir. Aşağıda birkaç matrisleri gösterilmektedir.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Ayrı ayrı öğeler ekleyerek aynı boyutta iki matrisi ekleyebilirsiniz. Matris toplama iki örnekleri aşağıda gösterilmiştir.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 Bir m × n matris n × p matris tarafından çarpılacağı ve m × p matris sonucudur. İlk Matristeki sütun sayısı ikinci matrisin satır sayısı ile aynı olması gerekir. Örneğin, bir 4 × 2 matris 4 × 3 matris üretmek için 2 bir × 3 matris tarafından çarpılan.  
  
 Düzlemi ve satırları ve sütunları matrisin noktaları, vektörleri olarak düşünülebilir. Örneğin, (2, 5) olan bir vektör iki bileşenlerle ve (3, 7, 1) üç bileşenlerle vektör. İki vektör nokta çarpımını şu şekilde tanımlanır:  
  
 (a, b) • (c d) = ac + bd  
  
 (a, b, c) • (d, e, f) ad = + olması + cf  
  
 Örneğin, nokta çarpımını (2, 3) ve (5, 4) olan (2)(5) + (3)(4) = 22. Nokta ürün (2, 5, 1) ve (4, 3, 1) olan (2)(4) + (5)(3) + (1)(1) = 24. İki vektör nokta çarpımını bir sayı değil başka bir vektör olduğuna dikkat edin. Ayrıca, yalnızca iki vektörü bileşenleri aynı sayıda varsa nokta ürün hesaplayabilirsiniz unutmayın.  
  
 Let A(i, j) i satır ve jth sütunda bir matris girişi olması. Örneğin bir (3, 2) 3 satır ve 2 sütun A Matristeki giriştir. A, B ve C matrisleri ve AB olan varsayalım c = C girişlerinin şöyle hesaplanmıştır:  
  
 C (i, j) = (satır i a) • (sütun j b)  
  
 Matris çarpım bazı örnekleri aşağıda gösterilmiştir.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 1 matris × 2 düzlemi bir noktanın düşünüyorsanız, bu noktadan 2 × 2 matris tarafından çarparak dönüştürebilirsiniz. Aşağıdaki çizimde, (2, 1) noktasına uygulanan birkaç dönüşümler gösterir.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Yukarıdaki şekilde gösterildiği dönüşümleri doğrusal dönüşümler tümü. Çeviri gibi diğer bazı dönüşümleri doğrusal değildir ve tarafından 2 × 2 matris çarpım olarak ifade olamaz. İstediğiniz varsayalım başlamak noktası (2, 1), 90 derece döndürün, x yönünde 3 birimlerinde Çevir ve y yönünde 4 birimlerinde çevir. Bu, bir matris ekleyerek ve ardından bir matris çarpım kullanarak gerçekleştirebilirsiniz.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Bir çeviri (1 × 2 matris eklenmesi) ve ardından doğrusal dönüştürme (2 × 2 matris tarafından çarpma) bir afin dönüşümü adı verilir. Afin bir dönüştürme matrisi (bir doğrusal bölümü için) ve bir çeviri için bir çift depolamak için tüm dönüştürme 3 × 3 matrisinde depolamak için alternatiftir. Bunun çalışmasını sağlamak için düzlemi noktasında kukla 3 koordinat ile 1 × 3 Matristeki depolanmalıdır. Her zamanki teknik tüm 3 koordinatları 1'e eşit olmasını sağlamaktır. Örneğin, (2, 1) noktası [2 1 1] matris temsil edilir. Aşağıdaki çizimde bir afin dönüşümü gösterir (90 derece döndürün; Çevir 3 birimleri x yönünde, y yönünde 4 birimleri) tarafından tek 3 × 3 matris çarpım olarak ifade edilen.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 Önceki örnekte, (2, 1) noktası (2, 6) noktasına eşlenir. 3 × 3 matrisi üçüncü sütun sayıları 0, 0, 1 içerdiğine dikkat edin. Bu, her zaman bir afin dönüşümü 3 × 3 matrisin durumunda olacaktır. 1 ve 2 sütunlardaki altı sayıları önemli numaralarıdır. Sol üst 2 × 2 kısmını matris dönüştürme doğrusal bir parçası ve 3 satır ilk iki girdileri çeviri temsil eder.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 İçinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] afin dönüşümünde depolayabilir bir <xref:System.Drawing.Drawing2D.Matrix> nesnesi. Afin dönüşüm temsil eden bir matris üçüncü sütun her zaman olduğundan (0, 0, 1), yapısı oluştururken ilk iki sütunu yalnızca altı sayıları belirtmek bir <xref:System.Drawing.Drawing2D.Matrix> nesnesi. Deyim `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` Yukarıdaki çizimde gösterilen matris oluşturur.  
  
## <a name="composite-transformations"></a>Bileşik dönüşümler  
 Bileşik dönüştürme dönüşümleri, biri tarafından izlenen bir dizisidir. Matrisleri ve aşağıdaki listede dönüştürmeleri göz önünde bulundurun:  
  
|||  
|-|-|  
|Matris A|90 derece döndürün|  
|Matris B|2 x yönünde faktörüyle ölçeklendirme|  
|Matris C|Y yönünde 3 birimlerinde Çevir|  
  
 Biz noktası (2, 1) ile başlatırsanız — [2 1 1] matris tarafından temsil edilen — ve C, listelenen sırayla üç Dönüşümleri (2, 1) noktası yapılacaktır sonra A, ardından B tarafından çarpın.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Bunun yerine bileşik dönüştürme üç bölümden içinde üç ayrı matrisleri depoladığınızdan, A çarpabilirsiniz B ve C birlikte tüm bileşik dönüştürme depolar tek bir 3 × 3 matris alınamıyor. ABC varsayalım D. = Ardından D çarpılan bir noktası A, ardından B, ardından C. çarpılan noktası aynı sonucu verir  
  
 [2 1 1] D = [-2, 5, 1]  
  
 Aşağıdaki çizimde A, B, C ve D. matrisleri gösterir  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Afin dönüşümler herhangi bir dizi tek bir depolanabilir bileşik bir dönüştürme matrisi tek tek Dönüştürme Matrislerini çarparak oluşturulmuş olduğunu olgu anlamına gelir <xref:System.Drawing.Drawing2D.Matrix> nesnesi.  
  
> [!CAUTION]
>  Bileşik dönüştürme sırası önemlidir. Genel olarak, döndürme, Ölçek, sonra aynı olan Çevir ölçek olarak döndürme, sonra çevir. Benzer şekilde, matris çarpım sırası önemlidir. Genel olarak, ABC İCLOU ile aynı değil.  
  
 <xref:System.Drawing.Drawing2D.Matrix> Sınıfı, bileşik bir dönüşüm oluşturmaya yönelik birkaç yöntem sağlar: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, ve <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>. Aşağıdaki örnek, ilk 30 derece döner sonra 2. y yönünde faktörüyle ölçeklendirir ve 5 birim x yönünde çevirir bileşik bir dönüştürme matrisi oluşturur:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 Aşağıdaki çizimde matrisi gösterir.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koordinat Sistemleri ve Dönüştürmeler](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Yönetilen GDI+'da Dönüştürmeleri Kullanma](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
