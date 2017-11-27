---
title: "Nasıl yapılır: Doğrusal Gradyan Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbf3b1657a5a6b91ba88a0968b6b92d4e4bdbf0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-linear-gradient"></a>Nasıl yapılır: Doğrusal Gradyan Oluşturma
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Yatay, dikey ve Çapraz doğrusal gradyanlar sağlar. Varsayılan olarak, doğrusal gradyan rengi aynı şekilde değiştirir. Bununla birlikte, böylece Tekdüzen olmayan biçimde rengi değişir doğrusal gradyan özelleştirebilirsiniz.  
  
 Aşağıdaki örnek, bir satırı, elips ve dikdörtgen Yatay doğrusal gradyan fırçası ile doldurur.  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu dört bağımsız değişkenleri alır: iki nokta ve iki rengi. İlk (0, 10) ilk rengi (kırmızı) ile ilişkili noktasıdır ve ikinci bir nokta (200, 10) ikinci rengi (mavi) ile ilişkilendirilir. Gelen çizgi beklediğiniz gibi (0, 10) için (200, 10) değişiklikleri kademeli olarak mavi ve kırmızı.  
  
 10'luk bloklar noktaları (50, 10) ve (200, 10) önemli değildir. Önemli olan iki nokta aynı ikinci koordinat olmasıdır — bunları bağlayan bir çizgi yataydır. Elips ve dikdörtgen ayrıca kademeli olarak yatay koordinat 200'e 0'dan geçtikçe mavi ve kırmızı gelen değiştirin.  
  
 Aşağıdaki çizimde, satır, elips ve dikdörtgen gösterir. Yatay koordinat 200 arttıkça renk gradyan kendisini tekrarlar olduğunu unutmayın.  
  
 ![Doğrusal gradyan](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>Yatay doğrusal gradyanlar kullanmak için  
  
-   Donuk kırmızı ve donuk mavi renkte sırasıyla üçüncü ve dördüncü bağımsız değişken olarak geçirin.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 Yatay koordinatını 200 için yatay koordinatını 0 taşımak gibi önceki örnekte, renk bileşenleri doğrusal olarak değiştirin. Örneğin, ilk koordinat 0 ve 200 arasında ortasında yer alan bir noktası 0 ile 255 arasında ortasında yer alan mavi bir bileşen sahip olur.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]bir renk bir gradyan kenarından değişir şekilde ayarlamanıza olanak sağlar. Kırmızı aşağıdaki tabloya göre siyah değişikliklerini bir gradyan fırçası oluşturmak istediğinizi varsayalım.  
  
|Yatay koordinat|RGB bileşenleri|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 Yatay koordinat 200 0'dan şekilde yüzde 20'yalnızca olduğunda kırmızı bileşenini yarım yoğunlukta olduğuna dikkat edin.  
  
 Aşağıdaki örnek kümeleri <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> özelliği bir <xref:System.Drawing.Drawing2D.LinearGradientBrush> üç göreli yoğunluklarda üç göreli konumları ile ilişkilendirmek için nesne. Önceki tabloda olduğu gibi göreli bir 0,5 yoğunluğunu göreli konumunu 0.2 ile ilişkilidir. Kod elips ve dikdörtgen gradyan fırçası ile doldurur.  
  
 Aşağıdaki çizimde sonuçta elde edilen elips ve dikdörtgen gösterir.  
  
 ![Doğrusal gradyan](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")  
  
### <a name="to-customize-linear-gradients"></a>Doğrusal gradyanlar özelleştirmek için  
  
-   Donuk siyah ve donuk kırmızıyla sırasıyla üçüncü ve dördüncü bağımsız değişken olarak geçirin.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 Önceki örneklerde gradyan yatay; diğer bir deyişle, renk yatay bir çizgi boyunca taşırken kademeli olarak değiştirir. Ayrıca, dikey gradyanlar ve Çapraz Gradyan tanımlayabilirsiniz.  
  
 Aşağıdaki örnek noktaları (0, 0) ve (200, 100) geçirir bir <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu. Mavi ilişkili olduğu (0, 0) ve yeşil ilişkili olduğu (200, 100). Bir çizgiyle (Kalem genişliği 10) ve elips doğrusal gradyan fırçası ile doldurulur.  
  
 Aşağıdaki çizimde satır ve üç nokta gösterir. Not taşırken elips değişiklikleri rengi kademeli olarak satırında aracılığıyla geçirme satırına paralel (0, 0) ve (200, 100).  
  
 ![Doğrusal gradyan](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>Çapraz doğrusal gradyanlar oluşturmak için  
  
-   Donuk mavi ve donuk yeşil sırasıyla üçüncü ve dördüncü bağımsız değişken olarak geçirin.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şekilleri doldurmak için gradyan fırçası kullanma](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [Grafikler ve Windows Forms'ta çizme](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
