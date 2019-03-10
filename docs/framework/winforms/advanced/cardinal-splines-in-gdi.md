---
title: GDI+'daki Ana Eğri Cetvelleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
ms.openlocfilehash: 6cc57698c8e43aefff0e0a63b0384417483d3b48
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705291"
---
# <a name="cardinal-splines-in-gdi"></a>GDI+'daki Ana Eğri Cetvelleri
Kardinal eğri bireysel eğrilerinin daha büyük bir eğri oluşturmak üzere birleştirilmiş bir dizidir. Eğri, bir dizi noktaları ve gerilimi parametresi tarafından belirtilir. Kardinal eğri sorunsuz dizideki her noktası üzerinden geçirir; hiçbir keskin köşeleri ve eğrinin tightness ani hiçbir değişiklik vardır. Aşağıdaki çizimde, bir dizi noktaları ve her nokta kümesi içinde geçtiği bir Kardinal eğri gösterir.  
  
 ![Kardinal eğri](./media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>Fiziksel ve matematik eğrileri  
 Fiziksel bir eğri Ahşap veya esnek diğer malzemeleri ince bir parçasıdır. Matematik eğrileri gelişinden önce tasarımcılar, eğriler çizmek için fiziksel eğrileri kullanılır. Bir tasarımcı bir kağıda eğri yerleştirin ve belirli bir nokta kümesi için bağlantı. Tasarımcı daha sonra bir eğri Eğri boyunca çizerek bir kalem ve kağıt ile oluşturabilirsiniz. Belirli bir nokta kümesi Eğriler, fiziksel eğri özelliklerine bağlı olarak çeşitli üretebilir. Örneğin, bir eğri döndürme yüksek Direnç ile son derece esnek bir eğri değerinden farklı bir eğri oluşturur.  
  
 Matematik eğrileri tarafından üretilen eğrileri fiziksel eğrileri tarafından üretilmiş bir kez eğrileri benzer şekilde formülleri matematik eğrileri için esnek Çubuklar özellikleri temel alır. Yalnızca farklı gerilimi, fiziksel eğrileri noktaları belirli bir dizi aracılığıyla farklı eğrileri oluşturacak şekilde gerilimi parametresi için farklı değerlerle matematik eğrileri farklı eğrileri noktaları belirli bir dizi aracılığıyla oluşturur. Aşağıdaki çizimde, dört Eğriler aynı dizi noktaları aracılığıyla geçirme gösterir. Her bir eğri için gerilimi gösterilmektedir. Bir gerilimi 0 noktaları arasında en kısa yolu (düz çizgiler) gerçekleştirilecek eğrisi zorlanması sonsuz fiziksel gerilimi karşılık gelir. 1 bir gerilimi eğri az toplam dirseği yolunu almak izin yok fiziksel gerilimi karşılık gelir. 1'den büyük gerilimi değerleri ile daha uzun yoldan şuraya gönderildi eğri sıkıştırılmış bir spring gibi davranır.  
  
 ![Ana eğri cetvelleri](./media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 Önceki çizimde dört eğrileri başlangıç noktası aynı Eğim satırında paylaşın. Tanjantı başlangıç noktasından sonraki noktaya eğri çizgi ' dir. Benzer şekilde, paylaşılan tanjantını bitiş noktasında bitiş noktasından önceki noktaya eğri çizgi ' dir.  
  
 Kardinal eğri çizme için örneği gerekir <xref:System.Drawing.Graphics> sınıfı, bir <xref:System.Drawing.Pen>ve bir dizi <xref:System.Drawing.Point> örneğini nesneleri <xref:System.Drawing.Graphics> sağlar sınıfını <xref:System.Drawing.Graphics.DrawCurve%2A> eğrisi çizer, yöntemi ve <xref:System.Drawing.Pen> çizgi genişliği ve rengine gibi Eğri özniteliklerini depolar. Dizi <xref:System.Drawing.Point> nesneleri eğri geçirilmesi noktalarını depolar. Aşağıdaki kod örneği noktaları geçtiği bir Kardinal eğri çizme gösterilmiştir `myPointArray`. Üçüncü gerilimi parametredir.  
  
 [!code-csharp[LinesCurvesAndShapes#31](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Eğriler Oluşturma ve Çizme](constructing-and-drawing-curves.md)
