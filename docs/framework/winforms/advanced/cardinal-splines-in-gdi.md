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
ms.openlocfilehash: 93ae09c72415fa489e62f753e51e5a3ffcfb2425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517971"
---
# <a name="cardinal-splines-in-gdi"></a>GDI+'daki Ana Eğri Cetvelleri
Kardinal eğri daha büyük bir eğri oluşturmak için birleştirilmiş tek tek Eğriler dizisidir. Eğri bir dizi noktaları ve gerilim parametresi tarafından belirtilir. Kardinal eğri her bir dizi noktası sorunsuz geçtiği; hiçbir keskin köşeleri ve eğri tightness ani hiçbir değişiklik vardır. Aşağıdaki çizimde bir dizi noktaları ve kümedeki her noktası geçtiği bir Kardinal eğri gösterir.  
  
 ![Kardinal eğri](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>Fiziksel ve matematiksel eğrileri  
 Fiziksel bir eğri wood veya esnek diğer malzemelerin ince bir parçasıdır. Matematik eğrileri geliştirilirken önce tasarımcıları fiziksel eğrileri eğriler çizmek için kullanılır. Bir tasarımcı eğri bir kağıda yerleştirin ve ancak belirli bir nokta kümesi için bağlantı. Tasarımcı daha sonra bir eğri Eğri boyunca çizerek bir kalem veya kalem oluşturabilirsiniz. Belirli bir nokta kümesi Eğriler, fiziksel eğri özelliklerini bağlı olarak çeşitli üretebilir. Örneğin, bir eğri döndürme yüksek Direnç ile son derece esnek bir eğri den farklı bir eğri üretir.  
  
 Matematik eğrileri tarafından üretilen Eğriler kez fiziksel eğrileri tarafından üretilmiş olan Eğriler benzer şekilde formülleri matematiksel eğrileri için esnek Çubuklar özelliklerini temel alır. Farklı gerilim, fiziksel eğrileri noktaları belirli bir dizi farklı Eğriler yalnızca oluşturacak şekilde gerilim parametresi için farklı değerler ile matematiksel eğrileri noktaları belirli bir dizi farklı Eğriler oluşturur. Aşağıdaki çizimde, dört Eğriler noktaları aynı dizi ile geçirme gösterir. Her eğri için gerilimi gösterilir. Gerilim 0 (düz çizgiler) noktaları arasında en kısa yolu yapılacak eğri zorlama sonsuz fiziksel gerilim karşılık gelir. Gerilim 1 az toplam dirseği yolunu yapılacak eğri izin vererek hiçbir fiziksel gerilim karşılık gelir. Gerilim ile 1'den büyük değerler, uzun bir yol olması için gönderilen eğri sıkıştırılmış bir yay gibi davranır.  
  
 ![Eğriler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 Önceki çizimde dört eğrileri başlangıç noktası aynı Eğim satırında paylaşır. Tanjantını başlangıç noktasından eğri bir sonraki noktasına çizgi ' dir. Benzer şekilde, paylaşılan tanjantını bitiş noktasında bitiş noktasından önceki noktasına eğri çizgi ' dir.  
  
 Kardinal eğri çizmek için örneği gerekir <xref:System.Drawing.Graphics> sınıfı, bir <xref:System.Drawing.Pen>ve bir dizi <xref:System.Drawing.Point> örneğini nesneleri <xref:System.Drawing.Graphics> sınıfı sağlar <xref:System.Drawing.Graphics.DrawCurve%2A> eğri çizer, yöntemi ve <xref:System.Drawing.Pen> çizgi genişliği ve renk gibi Eğri özniteliklerini depolar. Dizi <xref:System.Drawing.Point> nesnelerini eğri geçirilir noktalarını depolar. Aşağıdaki kod örneğinde nasıl noktaları geçtiği bir Kardinal eğri çizileceğini gösterir `myPointArray`. Gerilim üçüncü parametresidir.  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Eğriler Oluşturma ve Çizme](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
