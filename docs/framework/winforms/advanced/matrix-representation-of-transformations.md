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
ms.openlocfilehash: ceaad7b4bb5a70a890d261e39bc608becb388c17
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505630"
---
# <a name="matrix-representation-of-transformations"></a>Dönüşümlerin Matrisle Temsili
M × n matris m satırları ve sütunları n düzenlenen numaraları kümesidir. Aşağıdaki resimde, birkaç matrislerde gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Tek tek öğelerine ekleyerek aynı boyutta iki matrislerde ekleyebilirsiniz. Matris Ayrıca iki örnekleri aşağıda gösterilmiştir.  
  
 ![Dönüşümler](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 Bir milyon × n matris bir n × p matris ile çarpılmasına ve bir m × p matris sonucudur. İlk Matris sütun sayısı, ikinci matrisin satır sayısı ile aynı olmalıdır. Örneğin, 4 × 2 matris 4 x 3 matris üretmek için 2 bir × 3 matris ile çarpılmasına.  
  
 Düzlem ve satırları ve sütunları bir matris noktaları, vektör olarak düşünülebilir. Örneğin, (2, 5) olan bir vektörü iki bileşenlerle ve (3, 7, 1) üç bileşeni ile bir vektördür. İki vektörün nokta çarpımını şu şekilde tanımlanır:  
  
 (a, b) • (c, d) = ac + bd  
  
 (a, b, c) • (d, e, f) ad = + olması + cf  
  
 Örneğin, nokta çarpımını (2, 3) ve (5, 4) olduğunu (2)(5) + (3)(4) 22 =. (2, 5, 1) nokta çarpımını ve (4, 3, 1) olan (2)(4) + (5)(3) + (1)(1) = 24. İki vektörün nokta çarpımını bir sayı değil başka bir vektör olduğuna dikkat edin. Ayrıca, yalnızca iki vektörün aynı sayıda bileşen varsa nokta çarpımını hesaplayabilirsiniz unutmayın.  
  
 İzin A(i, j) i. satır ve jth sütunda bir matris girişi olabilir. Örneğin bir (3, 2) A Matristeki 3 satır ve 2 Sütun giriş. Matrisler ve AB A, B ve C olan varsayalım c = Girişleri c şu şekilde hesaplanır:  
  
 C (i, j) = (satır i a) • (b sütun j)  
  
 Matris çarpım bazı örnekleri aşağıda gösterilmiştir.  
  
 ![Dönüşümler](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Bir noktanın 1 × 2 matris olarak düzlemde düşünüyorsanız, 2 × 2 matris ile çarpılarak o noktadan dönüştürebilirsiniz. (2, 1) noktasına uygulanan çeşitli dönüşümler aşağıda gösterilmiştir.  
  
 ![Dönüşümler](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Yukarıdaki şekilde gösterilen dönüştürmeleri doğrusal dönüşümler tümü. Çeviri gibi diğer bazı dönüştürmeleri doğrusal değildir ve 2 × 2 matris çarpım olarak ifade edilemez. İstediğiniz varsayalım başlamak noktası (2, 1) 90 derece döndür 3 birim x yönünde çevirir ve 4 birimi y yönünde çevirir. Bu, bir matris ekleyerek ve ardından bir matris çarpım kullanarak gerçekleştirebilirsiniz.  
  
 ![Dönüşümler](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Bir çeviri (1 × 2 matrisin ek olarak) ve ardından bir doğrusal dönüştürme (2 × 2 matris çarpım) afin bir dönüştürme çağrılır. Afin bir dönüştürme matrisi (bir doğrusal bölümü için) ve bir çeviri için bir çift depolamak için bir alternatif, tüm dönüşümü 3 × 3 matriste depolamaktır. Bunun çalışmasını sağlamak için masasında bir noktadan kukla 3 koordinat 1 × 3 sunulmakta depolanması gerekir. Tüm 3 koordinatları 1'e eşit hale getirmek için her zamanki tekniktir bakın. Örneğin, (2, 1) noktası [2, 1, 1] matris tarafından temsil edilir. Afin bir dönüştürme aşağıdaki çizimde (90 derece Döndür; Çevir 3 birim x yönünde, y yönünde 4 birimi) tek 3 × 3 matris çarpım olarak ifade edilir.  
  
 ![Dönüşümler](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 Önceki örnekte, (2, 1) noktası noktası (2, 6) eşlenmiş. Üçüncü sütunda 3 × 3 matris numaraları 0, 0, 1 içerdiğine dikkat edin. Bu, her zaman bir afin dönüşümü 3 × 3 matris olayı olacaktır. Önemli rakamları 1 ve 2 sütunlardaki altı sayılardır. Matris sol 2 × 2 bölümüne dönüştürme doğrusal bir parçası ve çeviri 3 satır ilk iki girişleri temsil eder.  
  
 ![Dönüşümler](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 GDI +'da bir afin dönüşümünde depolayabileceğiniz bir <xref:System.Drawing.Drawing2D.Matrix> nesne. Üçüncü sütunda bir afin dönüşümü temsil eden bir matris her zaman olduğundan (0, 0, 1) oluşturduğunuzda, ilk iki sütunlarda yalnızca altı numaralarını belirtme bir <xref:System.Drawing.Drawing2D.Matrix> nesne. Deyim `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` önceki şekilde gösterildiği matris oluşturur.  
  
## <a name="composite-transformations"></a>Bileşik dönüşümler  
 Bileşik bir dönüştürme, Dönüşümlerin, biri tarafından izlenen bir dizidir. Matrisler ve dönüştürmeleri aşağıdaki listede göz önünde bulundurun:  
  
|||  
|-|-|  
|Matrix A|90 derece döndür|  
|Matrix B|2 x yönünde faktörüyle ölçeklendirin|  
|Matrix C|Y yönünde 3 birim Çevir|  
  
 Biz noktası (2, 1) ile başlatırsanız — [2, 1, 1] matris tarafından temsil edilen — ve tarafından sonra A, B, C, (2, 1) noktası listelendikleri sırada üç dönüştürmeleri yapılacaktır sonra çarpın.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Bunun yerine bileşik dönüşümü üç parça üç ayrı matrislerde depoladığınızdan, A çarpabilirsiniz B ve C birlikte tüm bileşik dönüşümü depolar tek bir 3 × 3 matris alınamıyor. ABC varsayalım d = Ardından D çarpılan bir noktası A, ardından B, C. daha sonra çarpılan bir noktası olarak aynı sonucu verir.  
  
 [2 1 1]D = [-2 5 1]  
  
 Aşağıdaki çizim A, B, C ve d matrislerde gösterir  
  
 ![Dönüşümler](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Bileşik bir dönüştürme matrisi tek bir dönüştürme matrisi çarpılarak oluşturulabilir afin dönüşümler herhangi bir dizi tek bir depolanabilir anlamına gelir <xref:System.Drawing.Drawing2D.Matrix> nesne.  
  
> [!CAUTION]
>  Bileşik bir dönüştürme sırası önemlidir. Genel olarak, döndürme, ölçeklendirme, sonra aynı olan Çevir ölçek olarak döndürün, sonra çevir. Benzer şekilde, matris çarpım sırası önemlidir. Genel olarak, ABC arka ile aynı değil.  
  
 <xref:System.Drawing.Drawing2D.Matrix> Sınıfı bir bileşik dönüşümü oluşturmak için çeşitli yöntemler sağlar: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, ve <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>. Aşağıdaki örnek, ilk 30 derece döndürür sonra y yönünde 2'in göre ölçeklenen ve ardından 5 birim x yönünde çevirir bileşik bir dönüştürme matrisini oluşturur:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 Matris aşağıda gösterilmiştir.  
  
 ![Dönüşümler](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koordinat Sistemleri ve Dönüştürmeler](coordinate-systems-and-transformations.md)
- [Yönetilen GDI+'da Dönüştürmeleri Kullanma](using-transformations-in-managed-gdi.md)
