---
title: Expressions2
ms.date: 03/30/2017
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
ms.openlocfilehash: 2f08e114729d9fd00a51fe0c4182862257e8c330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515974"
---
# <a name="expressions"></a>İfadeler
Bu örnek temel ifadeleri bir iş akışında kullanmayı gösterir. İki kurgusal bir şirkette çalışanlar için temel maaş istatistikleri hesaplar bir iş akışı oluşur. İki sınıf `Employee` ve `SalaryStats`, Employee.cs ve SalaryStats.cs tanımlanır. Bu sınıfların basit aritmetik ve dize değişkenleri özelliklerini, karmaşık türler işlemleri gösteren bir iş akışında kullanılır.  
  
 Maaş hesaplama iş akışı XAML hem de iki geliştirme stilleri göstermek için C# tanımlanır. XAML sürüm SalaryCalculation.xaml içinde yer alan ve görüntülenebilir ve iş akışı Tasarımcısı'nda düzenlenemez. C# sürümü Program.cs içinde bulunur. XAML'de kullanılan ifadeleri Visual Basic sözdizimine uygun olması ve kullanmak <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ve <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> ifade etkinliklerinin yürütülmesine. Visual Basic ifadeleri bakın hakkında daha fazla bilgi için [Visual Basic ifadeleri](http://go.microsoft.com/fwlink/?LinkId=165912). Diğer taraftan, C# ' ifadelerin lambda ifadeleri olarak yazılmıştır ve kullanmak <xref:System.Activities.Expressions.LambdaValue%601> ve <xref:System.Activities.Expressions.LambdaReference%601> ifade etkinlikler. Lambda ifadeleri olarak deyimleri yazarken sözdizimi vurgulama sağlamak için C# Derleyici ve statik doğrulama sağlar. C# ' deki lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri (C# programlama Kılavuzu)](http://go.microsoft.com/fwlink/?LinkId=182082). Visual Basic kullanarak kod içinde bir iş akışı yazılmışsa, Visual Basic lambda ifadeleri kullanılır. Visual Basic'te lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri (Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=152437). Kod kullanarak iş akışları yazma hakkında daha fazla bilgi için bkz: [geliştirme iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Expressions.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek veya seçmek için CTRL + SHIFT + B tuşuna basın **yapı çözümü** gelen **yapı** menüsü.  
  
    > [!NOTE]
    >  Visual Studio Tasarımcısı'nda SalaryCalculation.xaml açmak için ilk projeniz emin olmak için derleme gerekir `Employee` ve `SalaryStats` sınıfları Designer'a kullanılabilir.  
  
3.  Derleme başarılı olduktan sonra F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Alternatif olarak Ctrl + F5 tuşuna basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü hata ayıklama olmadan çalıştırma.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`