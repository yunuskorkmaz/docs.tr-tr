---
title: "Birlikte çalışma etkinliğini bir .NET Framework 4 iş akışında kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aa8bb873ed42d5ba717359f420855b605cbe423d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>Birlikte çalışma etkinliğini bir .NET Framework 4 iş akışında kullanma
Kullanılarak oluşturulan etkinlikleri [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] veya [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] kullanılabilir bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanarak iş akışı <xref:System.Activities.Statements.Interop> etkinlik. Bu konuda kullanarak genel bir bakış sağlar <xref:System.Activities.Statements.Interop> etkinlik.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> Etkinliği iş akışı Proje olmadıkça iş akışı Tasarımcısı Araç Kutusu'nda görünmez kendi **hedef Framework** ayarını **.Net Framework 4** veya sonraki bir sürümü.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>.NET Framework 4.5 akışlarında birlikte çalışma etkinliğini kullanma  
 Bu konuda, bir [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik kitaplığı oluşturulduğu içeren bir `DiscountCalculator` etkinlik. `DiscountCalculator` Satın alma miktarına bağlı bir indirim hesaplar ve oluşan bir <xref:System.Workflow.Activities.SequenceActivity> içeren bir <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Bu konuda oluşturulan etkinliği kullanan bir <xref:System.Workflow.Activities.PolicyActivity> etkinliğin mantığını uygulamak için. Özel bir kullanmak için gerekli olmayan [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik veya <xref:System.Activities.Statements.Interop> kullanmak için etkinlik kuralları içinde bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı. Kuralları kullanma örneği için bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanmadan iş akışı <xref:System.Activities.Statements.Interop> etkinliği bkz [.NET Framework 4.5 ilke etkinlik](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) örnek.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>.NET Framework 3.5 etkinlik kitaplığı projesi oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] seçip **yeni** ve ardından **proje...** gelen **dosya** menüsü.  
  
2.  Genişletme **diğer proje türleri** düğümünde **yüklü şablonlar** bölmesinde ve select **Visual Studio çözümleri**.  
  
3.  Seçin **boş çözüm** gelen **Visual Studio çözümleri** listesi. Tür `PolicyInteropDemo` içinde **adı** kutusuna ve tıklatın **Tamam**.  
  
4.  Sağ **PolicyInteropDemo** içinde **Çözüm Gezgini** seçip **Ekle** ve ardından **yeni proje...** .  
  
    > [!TIP]
    >  Varsa **Çözüm Gezgini** pencere görünür, select değil **Çözüm Gezgini** gelen **Görünüm** menüsü.  
  
5.  İçinde **yüklü şablonlar** listesinde **Visual C#** ve ardından **iş akışı**. Seçin **.NET Framework 3.5** .NET Framework sürüm aşağı açılan listesi ve ardından **iş akışı etkinlik kütüphanesini** gelen **şablonları** listesi.  
  
6.  Tür `PolicyActivityLibrary` içinde **adı** kutusuna ve tıklatın **Tamam**.  
  
7.  Sağ **Activity1.cs** içinde **Çözüm Gezgini** seçip **silmek**. Tıklatın **Tamam** onaylamak için.  
  
#### <a name="to-create-the-discountcalculator-activity"></a>DiscountCalculator etkinlik oluşturmak için  
  
1.  Sağ **PolicyActivityLibrary** içinde **Çözüm Gezgini** seçip **Ekle** ve ardından **etkinlik...** .  
  
2.  Seçin **etkinlikle (kod ayrımı)** gelen **Visual C# öğeleri** listesi. Tür `DiscountCalculator` içinde **adı** kutusuna ve tıklatın **Tamam**.  
  
3.  Sağ **DiscountCalculator.xoml** içinde **Çözüm Gezgini** seçip **görünümü kodu**.  
  
4.  Aşağıdaki üç özellikleri ekleyin `DiscountCalculator` sınıfı.  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Sağ **DiscountCalculator.xoml** içinde **Çözüm Gezgini** seçip **Görünüm Tasarımcısı**.  
  
6.  Sürükleme bir **İlkesi** etkinliğinden **Windows iş akışı v3.0** bölümünü **araç** sürükleyip bırakın **DiscountCalculator** etkinliği .  
  
    > [!TIP]
    >  Varsa **araç** pencere görünür, select değil **araç** gelen **Görünüm** menüsü.  
  
#### <a name="to-configure-the-rules"></a>Kurallarını yapılandırmak için  
  
1.  Yeni eklenen tıklatın **İlkesi** henüz seçili değilse seçmek için etkinlik.  
  
2.  Tıklatın **RuleSetReference** özelliğinde **özellikleri** penceresi seçin ve özellik sağındaki üç nokta düğmesini tıklatın.  
  
    > [!TIP]
    >  Varsa **özellikleri** pencere görünür değil, seçin **Özellikler penceresini** gelen **Görünüm** menüsü.  
  
3.  Seçin **yeni tıklatın...** .  
  
4.  Tıklatın **Kuralı Ekle**.  
  
5.  İçine aşağıdaki ifadeyi yazın **koşulu** kutusu.  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  İçine aşağıdaki ifadeyi yazın **sonra Eylemler** kutusu.  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  Tıklatın **Kuralı Ekle**.  
  
8.  İçine aşağıdaki ifadeyi yazın **koşulu** kutusu.  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. İçine aşağıdaki ifadeyi yazın **sonra Eylemler** kutusu.  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. Tıklatın **Kuralı Ekle**.  
  
11. İçine aşağıdaki ifadeyi yazın **koşulu** kutusu.  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. İçine aşağıdaki ifadeyi yazın **sonra Eylemler** kutusu.  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. İçine aşağıdaki ifadeyi yazın **başka eylemler** kutusu.  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. Tıklatın **Tamam** kapatmak için **kural kümesi düzenleyici** iletişim kutusu.  
  
15. Yeni oluşturulan emin <xref:System.Workflow.Activities.Rules.RuleSet> seçildiyse **adı** liste öğesini tıklatıp **Tamam**.  
  
16. Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
 Eklenen Kurallar `DiscountCalculator` etkinlik bu yordamda, aşağıdaki kod örneğinde gösterilir.  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 Zaman <xref:System.Workflow.Activities.PolicyActivity> yürütür, bu üç kuralları değerlendirin ve değiştirme `Subtotal`, `DiscountPercent`, ve `Total` özellik değerlerini `DiscountCalculator` istenen indirim hesaplamak için etkinlik.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>İle birlikte çalışma etkinliğini DiscountCalculator etkinliğini kullanma  
 Kullanılacak `DiscountCalculator` etkinliği içinde bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı, <xref:System.Activities.Statements.Interop> etkinliği kullanılır. Bu bölümdeki iki iş akışları oluşturulur ve bir kod ve bir iş akışı Tasarımcısı'nı kullanarak kullanarak hangi Göster nasıl kullanılacağını <xref:System.Activities.Statements.Interop> etkinlikle `DiscountCalculator` etkinlik. Aynı ana bilgisayar uygulamasını hem de iş akışları için kullanılır.  
  
#### <a name="to-create-the-host-application"></a>Ana bilgisayar uygulaması oluşturmak için  
  
1.  Sağ **PolicyInteropDemo** içinde **Çözüm Gezgini** seçip **Ekle**ve ardından **yeni proje...** .  
  
2.  Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listesinde seçilen ve seçin **iş akışı konsol uygulaması** gelen **Visual C# öğeleri** listesi.  
  
3.  Tür `PolicyInteropHost` içine **adı** kutusuna ve tıklatın **Tamam**.  
  
4.  Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **özellikleri**.  
  
5.  İçinde **hedef framework** aşağı açılan listesinde, seçimden değiştirme **.NET Framework 4 istemci profili** için **.NET Framework 4.5**. Tıklatın **Evet** onaylamak için.  
  
6.  Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** .  
  
7.  Seçin **PolicyActivityLibrary** gelen **projeleri** sekmesinde **Tamam**.  
  
8.  Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** .  
  
9. Seçin **System.Workflow.Activities**, **System.Workflow.ComponentModel**ve ardından **System.Workflow.Runtime** gelen **.NET**sekmesinde **Tamam**.  
  
10. Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **başlangıç projesi olarak ayarla**.  
  
11. Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
### <a name="using-the-interop-activity-in-code"></a>Birlikte çalışma etkinlik kod içinde kullanma  
 Bu örnekte, bir iş akışı tanımını içeren kodu kullanılarak oluşturulan <xref:System.Activities.Statements.Interop> etkinlik ve `DiscountCalculator` etkinlik. Bu iş akışını kullanarak çağrılan <xref:System.Activities.WorkflowInvoker> ve kural değerlendirme sonuçlarını konsolunu kullanarak yazılır bir <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Birlikte çalışma etkinlik kodda kullanmak için  
  
1.  Sağ **Program.cs** içinde **Çözüm Gezgini** seçip **görünümü kodu**.  
  
2.  Aşağıdakileri ekleyin `using` deyimini dosyanın üst.  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  İçeriği Kaldır `Main` yöntemi ve aşağıdaki kod ile değiştirin.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  İçinde yeni bir yöntem oluşturma `Program` adlı bir sınıf `CalculateDiscountUsingCodeWorkflow` aşağıdaki kodu içerir.  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  `Subtotal`, `DiscountPercent`, Ve `Total` özelliklerini `DiscountCalculator` etkinlik bağımsız ortaya <xref:System.Activities.Statements.Interop> etkinliği ve yerel ilişkili iş akışı değişken <xref:System.Activities.Statements.Interop> etkinliğin <xref:System.Activities.Statements.Interop.ActivityProperties%2A> koleksiyonu. `Subtotal`eklenen bir <xref:System.Activities.ArgumentDirection.In> bağımsız değişkeni çünkü `Subtotal` veri akışları içine <xref:System.Activities.Statements.Interop> etkinlik, ve `DiscountPercent` ve `Total` olarak eklenir <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenler dışı kendi veri akışları için <xref:System.Activities.Statements.Interop> etkinlik. Unutmayın iki <xref:System.Activities.ArgumentDirection.Out> bağımsız değişken adlarıyla eklenen `DiscountPercentOut` ve `TotalOut` temsil ettikleri belirtmek için <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenler. `DiscountCalculator` Türü olarak belirtildiğinde <xref:System.Activities.Statements.Interop> etkinliğin <xref:System.Activities.Statements.Interop.ActivityType%2A>.  
  
5.  Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşuna basın. Yedek için farklı değerler `Subtotal` tarafından sağlanan farklı indirim düzeyleri çıkışı test etmek için değer `DiscountCalculator` etkinlik.  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Birlikte çalışma etkinliğini iş akışı Tasarımcısı'nda kullanma  
 Bu örnekte, bir iş akışı, iş akışı Tasarımcısı'nı kullanarak oluşturulur. Bu iş akışı önceki örnekte, aynı işlevselliği dışında daha kullanmak yerine sahip bir <xref:System.Activities.Statements.WriteLine> indirim görüntülenecek etkinlik konak uygulama alır ve iş akışı tamamlandığında indirim bilgilerini görüntüler. Ayrıca, yerine yerel iş akışı değişkenleri verileri içerecek şekilde, bağımsız değişkenler iş akışı Tasarımcısı'nda oluşturulur ve iş akışı çağrıldığında değerler, ana bilgisayardan geçirilir.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>İş Akışı Tasarımcısı tarafından oluşturulan bir iş akışını kullanarak PolicyActivity barındırmak için  
  
1.  Sağ **Workflow1.xaml** içinde **Çözüm Gezgini** seçip **silmek**. Tıklatın **Tamam** onaylamak için.  
  
2.  Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe...** .  
  
3.  Genişletme **Visual C# öğeleri** düğümü ve select **iş akışı**. Seçin **etkinlik** gelen **Visual C# öğeleri** listesi.  
  
4.  Tür `DiscountWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.  
  
5.  Tıklatın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı sol alt köşesine düğmesinde **bağımsız değişkenleri** bölmesi.  
  
6.  Tıklatın **bağımsız değişkeni oluşturma**.  
  
7.  Tür `Subtotal` içine **adı** kutusunda **içinde** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** aşağı açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
    > [!NOTE]
    >  Varsa **çift** bulunmayan **bağımsız değişken türü** aşağı açılan listesinden, **türleri için Gözat...** , türü `System.Double` içinde **türü adı** ve'ı tıklatın **Tamam**.  
  
8.  Tıklatın **bağımsız değişkeni oluşturma**.  
  
9. Tür `DiscountPercent` içine **adı** kutusunda **çıkışı** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** aşağı açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
10. Tıklatın **bağımsız değişkeni oluşturma**.  
  
11. Tür `Total` içine **adı** kutusunda **çıkışı** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** aşağı açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
12. Tıklatın **bağımsız değişkenleri** kapatmak için iş akışı Tasarımcısı sol alt köşesine düğmesinde **bağımsız değişkenleri** bölmesi.  
  
13. Sürükleme bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç** ve iş akışı Tasarımcı yüzeyine bırakın.  
  
14. Sürükleme bir **birlikte çalışabilirliği** etkinliğinden **geçiş** bölümünü **araç** sürükleyip bırakın **dizisi** etkinlik.  
  
15. Tıklatın **birlikte çalışabilirliği** faaliyete **göz atmak için tıklatın...** Etiket, yazın **DiscountCalculator** içinde **türü adı** ve'ı tıklatın **Tamam**.  
  
    > [!NOTE]
    >  Zaman <xref:System.Activities.Statements.Interop> etkinlik, iş akışına eklenir ve `DiscountCalculator` türü olarak belirtildiğinde kendi <xref:System.Activities.Statements.Interop.ActivityType%2A>, <xref:System.Activities.Statements.Interop> etkinlik üç gösterir <xref:System.Activities.ArgumentDirection.In> bağımsız değişkenleri ve üç <xref:System.Activities.ArgumentDirection.Out> üç genel temsil eden bağımsız değişkenler özelliklerini `DiscountCalculator` etkinlik. <xref:System.Activities.ArgumentDirection.In> Bağımsız değişkenleri üç genel özellikleri ve üç aynı ada sahip <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenleri ile aynı ada sahip **çıkışı** özellik adı eklenir. Aşağıdaki adımlarda, önceki adımlarda oluşturduğunuz iş akışı değişkenleri bağlı <xref:System.Activities.Statements.Interop> etkinliğin bağımsız değişkenler.  
  
16. Tür `DiscountPercent` içine **bir VB ifadesi girin** kutusunun sağındaki **DiscountPercentOut** özelliği ve SEKME tuşuna basın.  
  
17. Tür `Subtotal` içine **bir VB ifadesi girin** kutusunun sağındaki **alt toplam** özelliği ve SEKME tuşuna basın.  
  
18. Tür `Total` içine **bir VB ifadesi girin** kutusunun sağındaki **TotalOut** özelliği ve SEKME tuşuna basın.  
  
19. Sağ **Program.cs** içinde **Çözüm Gezgini** seçip **görünümü kodu**.  
  
20. Aşağıdakileri ekleyin `using` deyimini dosyanın üst.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. Açıklama çağrısı çıkışı `CalculateDiscountInCode` yönteminde `Main` yöntemi ve aşağıdaki kodu ekleyin.  
  
    > [!NOTE]
    >  Önceki yordamda ve varsayılan takip ettiğiniz değil, `Main` kodu varsa, Değiştir `Main` aşağıdaki kod ile.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. İçinde yeni bir yöntem oluşturma `Program` adlı bir sınıf `CalculateDiscountUsingDesignerWorkflow` aşağıdaki kodu içerir.  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşuna basın. Farklı bir belirtmek için `Subtotal` tutar, değerini değiştirme `SubtotalValue` aşağıdaki kodda.  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>Kuralları özelliklere genel bakış  
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] Kurallar altyapısı öncelik tabanlı bir şekilde İleri zincirleme desteğiyle kuralları işlemek için destek sağlar. Kurallar, bir koleksiyondaki öğelerin veya tek bir öğe için değerlendirilebilir. Kurallar ve belirli kurallar işlevselliği hakkında bilgi genel bakış için lütfen aşağıdaki tabloya bakın.  
  
|Kuralları özelliği|Belgeler|  
|-------------------|-------------------|  
|Kurallarına genel bakış|[Windows Workflow Foundation kurallar altyapısı giriş](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|RuleSet|[İş akışlarında RuleSets kullanarak](http://go.microsoft.com/fwlink/?LinkId=178516) ve<xref:System.Workflow.Activities.Rules.RuleSet>|  
|Kuralları değerlendirmesi|[RuleSets kuralları değerlendirmesine](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|Zincirleme kuralları|[İleri denetim zincirleme](http://go.microsoft.com/fwlink/?LinkId=178518) ve [İleri kuralları zincirleme](http://go.microsoft.com/fwlink/?LinkId=178519)|  
|Kural koleksiyonlarında işleme|[Kural koleksiyonlarında işleme](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|PolicyActivity kullanma|[Kullanarak PolicyActivity etkinliğini](http://go.microsoft.com/fwlink/?LinkId=178521) ve<xref:System.Workflow.Activities.PolicyActivity>|  
  
 Oluşturulan iş akışları [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] tarafından sağlanan tüm kuralları özelliklere kullanmayın [!INCLUDE[wf1](../../../includes/wf1-md.md)]bildirim temelli etkinlik koşullar ve gibi koşullu etkinlikler gibi <xref:System.Workflow.Activities.ConditionedActivityGroup> ve <xref:System.Workflow.Activities.ReplicatorActivity>. Gerekirse, bu işlevselliği kullanılarak oluşturulan iş akışları için kullanılabilir [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Geçiş Kılavuzu](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).
