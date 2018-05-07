---
title: 'Nasıl yapılır: Tarih ve Saat Değerlerinde Milisaniyeleri Görüntüleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7bf73920d10ff825396e61a3ca4e9efd622d9c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>Nasıl yapılır: Tarih ve Saat Değerlerinde Milisaniyeleri Görüntüleme
<xref:System.DateTime.ToString?displayProperty=nameWithType> gibi varsayılan tarih ve saat biçimlendirme yöntemleri, bir zaman değerinin saatlerini, dakikalarını ve saniyelerini içerir ancak milisaniye bileşenini içermez. Bu konu, biçimlendirilen tarih ve saat dizelerine bir tarihin ve saatin milisaniye bileşeninin nasıl eklendiğini gösterir.  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>Bir DateTime değerinin milisaniye bileşenini görüntülemek için  
  
1.  Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> değerine dönüştürün.  
  
2.  Bir saatin milisaniye bileşeninin dize gösterimini ayıklamak için, tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%2A> yöntemini çağırın ve `fff` veya `FFF` özel biçim desenini tek başına veya başka özel biçim tanımlayıcılarıyla birlikte `format` parametresi olarak geçirin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, her ikisi de tek başına olan ve daha uzun bir tarih ve saat dizesine eklenen bir <xref:System.DateTime> ve bir <xref:System.DateTimeOffset> değerine ait milisaniye bileşenini konsolda görüntüler.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 `fff` biçim deseni, milisaniye değerinin sonundaki sıfırları içerir. `FFF` biçim deseni bunları bastırır. Fark, aşağıdaki örnekte gösterilmiştir.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 Bir tarih ve saate ait milisaniye bileşenini içeren tam bir özel biçim tanımlayıcısını tanımlamadaki sorun, uygulamanın geçerli kültüründeki zaman öğelerinin düzenine karşılık gelmeyebilen sabit kodlanmış bir biçimi tanımlamasıdır. Daha iyi bir alternatif olarak geçerli kültürün <xref:System.Globalization.DateTimeFormatInfo> nesnesi tarafından tanımlanan tarih ve saat görüntüleme desenlerinden birini alıp milisaniye içerecek şekilde değiştirebilirsiniz. Örnek aynı zamanda bu yaklaşımı da gösterir. <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> özelliğinden geçerli kültürün tam tarih ve saat desenini alır ve ardından saniye deseninin sonrasına `.ffff` özel desenini ekler. Bu işlemi tek bir yöntem çağrısında gerçekleştirmek için örneğin bir normal ifade kullandığını unutmayın.  
  
 Saniyelerin milisaniye dışındaki kesirli bir kısmını görüntülemek için aynı zamanda özel bir biçim tanımlayıcısı da kullanabilirsiniz. Örneğin, `f` veya `F` özel biçim tanımlayıcısı bir saniyenin onda birini, `ff` veya `FF` özel biçim tanımlayıcısı bir saniyenin yüzde birini ve `ffff` veya `FFFF` özel biçim tanımlayıcısı bir saniyenin on binde birini görüntüler. Bir milisaniyenin kesirli kısımları döndürülen dizede yuvarlanmak yerine kesilir. Bu biçim tanımlayıcıları aşağıdaki örnekte kullanılır.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  Bir saniyenin on binde biri veya yüz binde biri gibi çok küçük kesirli birimlerini görüntülemek mümkündür. Ancak, bu değerler anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 ve üzeri sürümlerde ve [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] işletim sistemlerinde saatin çözünürlüğü yaklaşık olarak 10-15 milisaniyedir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu, csc.exe veya vb.exe kullanarak komut satırında derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulama projesi şablonunda yerleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
