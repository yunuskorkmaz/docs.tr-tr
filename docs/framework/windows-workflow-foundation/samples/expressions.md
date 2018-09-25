---
title: Expressions2
ms.date: 03/30/2017
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
ms.openlocfilehash: e852b62e6d0b6b4b3ddc19b197902de5325310a1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711369"
---
# <a name="expressions"></a>İfadeler
Bu örnek, temel ifadeleri bir iş akışında kullanmayı gösterir. Temel maaş istatistikleri hesaplar iki kurgusal bir şirkette çalışanlar için bir iş akışı oluşur. İki sınıf `Employee` ve `SalaryStats`, Employee.cs ve SalaryStats.cs tanımlanmış. Bu sınıfların nasıl basit aritmetik ve dizeyi değişkenleri özelliklerini karmaşık türleri işlemleri gösteren bir iş akışında kullanılır.  
  
 Ücret hesaplama iş akışı XAML hem de iki geliştirme stilleri göstermek için C# tanımlanır. XAML sürüm SalaryCalculation.xaml içinde yer alan ve görüntülenebilir ve iş akışı Tasarımcısı'nda düzenlenebilir. C# sürümü Program.cs içinde yer alıyor. XAML içinde kullanılan ifadeler, Visual Basic sözdizimine uygun olması ve kullanmak <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ve <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> ifade etkinlikleri yürütmek için. Visual Basic deyimleri bkz hakkında daha fazla bilgi için [Visual Basic deyimleri](https://go.microsoft.com/fwlink/?LinkId=165912). Öte yandan, C# ifadeleri lambda ifadeleri olarak yazılır ve kullanma <xref:System.Activities.Expressions.LambdaValue%601> ve <xref:System.Activities.Expressions.LambdaReference%601> ifade etkinlikleri. Lambda ifadeleri olarak ifadeleri yazarken, söz dizimi vurgulama sağlamak için C# derleyicisi ve statik doğrulama sağlar. C# ' deki lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri (C# programlama Kılavuzu)](https://go.microsoft.com/fwlink/?LinkId=182082). Daha sonra bir iş akışı Visual Basic kullanarak kod içinde yazılmışsa, Visual Basic lambda ifadeleri kullanılır. Visual Basic'te lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri (Visual Basic)](https://go.microsoft.com/fwlink/?LinkId=152437). Kod kullanarak iş akışları yazma hakkında daha fazla bilgi için bkz: [yazma iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Expressions.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derleyin veya seçmek için CTRL + SHIFT + B tuşlarına basın **Çözümü Derle** gelen **derleme** menüsü.  
  
    > [!NOTE]
    >  Visual Studio Tasarımcısı'nda SalaryCalculation.xaml açmak için önce emin olmak için projenizi derlemeniz gerekir `Employee` ve `SalaryStats` tasarımcıya sınıflar bulunur.  
  
3.  Derleme başarılı olana sonra F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Bunun yerine Ctrl + F5 tuşlarına basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** hata ayıklama olmadan çalıştırmak için menü.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`