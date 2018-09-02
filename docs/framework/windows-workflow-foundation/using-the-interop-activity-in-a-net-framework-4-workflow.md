---
title: Birlikte çalışma etkinliği bir .NET Framework 4 akışında kullanma
ms.date: 03/30/2017
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
ms.openlocfilehash: 02eeaf5bb7ff484ba5982197fc395e247cd5a87f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466731"
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>Birlikte çalışma etkinliği bir .NET Framework 4 akışında kullanma
Kullanılarak oluşturulan etkinlikleri [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] veya [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] kullanılabilir bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanarak iş akışı <xref:System.Activities.Statements.Interop> etkinlik. Bu konuda kullanarak genel bir bakış sağlar <xref:System.Activities.Statements.Interop> etkinlik.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> İş akışının proje sahip olmadığı sürece etkinlik iş akışı Tasarımcısı araç kutusunda görünmüyor, **hedef Framework'ü** ayarının **.Net Framework 4** veya üzeri.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>.NET Framework 4.5 iş akışlarında birlikte çalışma etkinliği kullanma  
 Bu konuda, bir [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik kitaplığı içeren oluşturulur bir `DiscountCalculator` etkinlik. `DiscountCalculator` Bir satın alma tutarını temel bir hesaplar ve oluşan bir <xref:System.Workflow.Activities.SequenceActivity> içeren bir <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Bu konu başlığında oluşturduğunuz etkinliğini kullanan bir <xref:System.Workflow.Activities.PolicyActivity> etkinliğin mantığını uygulamak için. Özel bir kullanmak için gerekli olmayan [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik veya <xref:System.Activities.Statements.Interop> kullanmak için etkinlik kuralları içinde bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı. Kuralları kullanma örneği için bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanmadan iş akışı <xref:System.Activities.Statements.Interop> etkinliğine bakın [.NET Framework 4. 5'te ilke etkinliği](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) örnek.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>.NET Framework 3.5 etkinliği kitaplık projesi oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] seçip **yeni** ardından **proje...** gelen **dosya** menüsü.  
  
2.  Genişletin **diğer proje türleri** düğümünde **yüklü şablonlar** bölmesi ve select **Visual Studio çözümleri**.  
  
3.  Seçin **boş çözüm** gelen **Visual Studio çözümleri** listesi. Tür `PolicyInteropDemo` içinde **adı** kutusuna ve tıklatın **Tamam**.  
  
4.  Sağ **PolicyInteropDemo** içinde **Çözüm Gezgini** seçip **Ekle** ardından **yeni proje...** .  
  
    > [!TIP]
    >  Varsa **Çözüm Gezgini** pencere görünür, select değil **Çözüm Gezgini** gelen **görünümü** menüsü.  
  
5.  İçinde **yüklü şablonlar** listesinden **Visual C#** ardından **iş akışı**. Seçin **.NET Framework 3.5** seçin ve .NET Framework sürümü açılır listede **iş akışı etkinlik Kitaplığı** gelen **şablonları** listesi.  
  
6.  Tür `PolicyActivityLibrary` içinde **adı** kutusuna ve tıklatın **Tamam**.  
  
7.  Sağ **Activity1.cs** içinde **Çözüm Gezgini** seçip **Sil**. Tıklayın **Tamam** onaylamak için.  
  
#### <a name="to-create-the-discountcalculator-activity"></a>DiscountCalculator etkinlik oluşturmak için  
  
1.  Sağ **PolicyActivityLibrary** içinde **Çözüm Gezgini** seçip **Ekle** ardından **etkinlik...** .  
  
2.  Seçin **etkinlik (kod ayırma ile)** gelen **Visual C# öğeleri** listesi. Tür `DiscountCalculator` içinde **adı** kutusuna ve tıklatın **Tamam**.  
  
3.  Sağ **DiscountCalculator.xoml** içinde **Çözüm Gezgini** seçip **kodu görüntüle**.  
  
4.  Aşağıdaki üç özelliği Ekle `DiscountCalculator` sınıfı.  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Sağ **DiscountCalculator.xoml** içinde **Çözüm Gezgini** seçip **Görünüm Tasarımcısı**.  
  
6.  Sürükleme bir **ilke** etkinliğinden **Windows iş akışı v3.0** bölümünü **araç kutusu** sürükleyip **DiscountCalculator** etkinliği .  
  
    > [!TIP]
    >  Varsa **araç kutusu** pencere görünür, select değil **araç kutusu** gelen **görünümü** menüsü.  
  
#### <a name="to-configure-the-rules"></a>Kurallarını yapılandırmak için  
  
1.  Yeni eklenen tıklayın **ilke** etkinliği zaten seçili değilse bunu seçin.  
  
2.  Tıklayın **RuleSetReference** özelliğinde **özellikleri** penceresini seçin ve özellik sağındaki elips düğmesine tıklayın.  
  
    > [!TIP]
    >  Varsa **özellikleri** penceresi görünür değilse, seçin **Özellikler penceresi** gelen **görünümü** menüsü.  
  
3.  Seçin **Yeni'ye tıklayın...** .  
  
4.  Tıklayın **Kuralı Ekle**.  
  
5.  İçine aşağıdaki ifadeyi yazın **koşul** kutusu.  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  İçine aşağıdaki ifadeyi yazın **ardından Eylemler** kutusu.  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  Tıklayın **Kuralı Ekle**.  
  
8.  İçine aşağıdaki ifadeyi yazın **koşul** kutusu.  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. İçine aşağıdaki ifadeyi yazın **ardından Eylemler** kutusu.  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. Tıklayın **Kuralı Ekle**.  
  
11. İçine aşağıdaki ifadeyi yazın **koşul** kutusu.  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. İçine aşağıdaki ifadeyi yazın **ardından Eylemler** kutusu.  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. İçine aşağıdaki ifadeyi yazın **başka eylemler** kutusu.  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. Tıklayın **Tamam** kapatmak için **kural kümesi Düzenleyicisi** iletişim kutusu.  
  
15. Yeni oluşturulan emin <xref:System.Workflow.Activities.Rules.RuleSet> seçili **adı** listesinde ve tıklayın **Tamam**.  
  
16. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
 Eklenen Kurallar `DiscountCalculator` etkinlik bu yordamda aşağıdaki kod örneğinde gösterilmiştir.  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 Zaman <xref:System.Workflow.Activities.PolicyActivity> yürütür, bu üç kuralları değerlendirin ve değiştirme `Subtotal`, `DiscountPercent`, ve `Total` özellik değerlerini `DiscountCalculator` istenen indirimi hesaplamak için etkinlik.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>Birlikte çalışma etkinliği ile DiscountCalculator etkinliği kullanma  
 Kullanılacak `DiscountCalculator` etkinliği içinde bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı, <xref:System.Activities.Statements.Interop> etkinliği kullanılır. Bu bölümde iki iş akışları oluşturulur, bir kod ve iş akışı Tasarımcısı kullanarak bir tane kullanarak gösteren nasıl kullanılacağını <xref:System.Activities.Statements.Interop> etkinliğiyle `DiscountCalculator` etkinlik. Aynı ana bilgisayar uygulaması hem de iş akışları için kullanılır.  
  
#### <a name="to-create-the-host-application"></a>Ana bilgisayar uygulaması oluşturmak için  
  
1.  Sağ **PolicyInteropDemo** içinde **Çözüm Gezgini** seçip **Ekle**, ardından **yeni proje...** .  
  
2.  Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listesinde seçili olduğunu doğrulayıp, seçin **iş akışı konsol uygulaması** gelen **Visual C# öğeleri** listesi.  
  
3.  Tür `PolicyInteropHost` içine **adı** kutusuna ve tıklatın **Tamam**.  
  
4.  Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **özellikleri**.  
  
5.  İçinde **hedef Framework'ü** aşağı açılan listesinde, seçimi değiştirme **.NET Framework 4 istemci profili** için **.NET Framework 4.5**. Tıklayın **Evet** onaylamak için.  
  
6.  Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** .  
  
7.  Seçin **PolicyActivityLibrary** gelen **projeleri** sekmesine **Tamam**.  
  
8.  Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** .  
  
9. Seçin **System.Workflow.Activities**, **System.Workflow.ComponentModel**, ardından **System.Workflow.Runtime** gelen **.NET**sekmesine **Tamam**.  
  
10. Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **başlangıç projesi olarak ayarla**.  
  
11. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
### <a name="using-the-interop-activity-in-code"></a>Kod içinde birlikte çalışma etkinliği kullanma  
 Bu örnekte, bir iş akışı tanımını içeren kod kullanılarak oluşturulan <xref:System.Activities.Statements.Interop> etkinlik ve `DiscountCalculator` etkinlik. Bu iş akışı kullanılarak çağrılan <xref:System.Activities.WorkflowInvoker> ve kuralı değerlendirme sonuçlarını konsolunu kullanarak yazılır bir <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Birlikte çalışma etkinliği kodu kullanmak için  
  
1.  Sağ **Program.cs** içinde **Çözüm Gezgini** seçip **kodu görüntüle**.  
  
2.  Aşağıdaki `using` deyimini dosyanın üst.  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  İçeriği kaldırmak `Main` yöntemi ve aşağıdaki kodla değiştirin.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  İçinde yeni bir yöntem oluşturma `Program` adlı sınıf `CalculateDiscountUsingCodeWorkflow` , aşağıdaki kodu içerir.  
  
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
    >  `Subtotal`, `DiscountPercent`, Ve `Total` özelliklerini `DiscountCalculator` etkinlik bağımsız değişkenleri ortaya <xref:System.Activities.Statements.Interop> etkinliği ve yerel ilişkili iş akışı değişkenleri <xref:System.Activities.Statements.Interop> etkinliğin <xref:System.Activities.Statements.Interop.ActivityProperties%2A> koleksiyonu. `Subtotal` olarak eklenir bir <xref:System.Activities.ArgumentDirection.In> bağımsız değişken olduğundan `Subtotal` veri akışları halinde <xref:System.Activities.Statements.Interop> etkinliği ve `DiscountPercent` ve `Total` olarak eklenir <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenleri tanesi kendi veri akışları için <xref:System.Activities.Statements.Interop> etkinlik. Unutmayın iki <xref:System.Activities.ArgumentDirection.Out> bağımsız değişken adları ile eklenen `DiscountPercentOut` ve `TotalOut` temsil ettikleri belirtmek için <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenler. `DiscountCalculator` Türü olarak belirtildiğinde <xref:System.Activities.Statements.Interop> etkinliğin <xref:System.Activities.Statements.Interop.ActivityType%2A>.  
  
5.  Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın. Yedek için farklı değerler `Subtotal` farklı indirim düzeyleri tarafından sağlanan çıkış test etmek için değer `DiscountCalculator` etkinlik.  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Birlikte çalışma etkinliği iş akışı Tasarımcısı'nda kullanma  
 Bu örnekte, iş akışı Tasarımcısı'nı kullanarak bir iş akışı oluşturulur. Bu iş akışı önceki örnekle aynı işlevselliği dışında daha kullanmak yerine sahip bir <xref:System.Activities.Statements.WriteLine> indirim görüntülemek için etkinliği ana bilgisayar uygulamasını alır ve iş akışı tamamlandığında indirim bilgilerini görüntüler. Ayrıca, verileri içerecek şekilde yerel iş akışı değişkenlerini kullanarak yerine bağımsız değişkenler iş akışı Tasarımcısı'nda oluşturulan ve iş akışı çağrıldığında değerleri konaktan geçirilir.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>Bir iş akışı tasarımcısı tarafından oluşturulan iş akışı kullanarak PolicyActivity barındırmak için  
  
1.  Sağ **Workflow1.xaml** içinde **Çözüm Gezgini** seçip **Sil**. Tıklayın **Tamam** onaylamak için.  
  
2.  Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe...** .  
  
3.  Genişletin **Visual C# öğeleri** düğümünü seçip alt **iş akışı**. Seçin **etkinlik** gelen **Visual C# öğeleri** listesi.  
  
4.  Tür `DiscountWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.  
  
5.  Tıklayın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı'nın bir alt sol taraftaki düğmeyi **bağımsız değişkenleri** bölmesi.  
  
6.  Tıklayın **bağımsız değişken oluşturma**.  
  
7.  Tür `Subtotal` içine **adı** kutusunda **içinde** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
    > [!NOTE]
    >  Varsa **çift** kullanımda olmayan **bağımsız değişken türü** aşağı açılan listesinden **vyhledat Typy...** , türü `System.Double` içinde **tür adı** ve'ı tıklatın **Tamam**.  
  
8.  Tıklayın **bağımsız değişken oluşturma**.  
  
9. Tür `DiscountPercent` içine **adı** kutusunda **kullanıma** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
10. Tıklayın **bağımsız değişken oluşturma**.  
  
11. Tür `Total` içine **adı** kutusunda **kullanıma** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
12. Tıklayın **bağımsız değişkenleri** iş akışı tasarımcısını kapatmak için sol alt köşesine düğmesinde **bağımsız değişkenleri** bölmesi.  
  
13. Sürükleme bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç kutusu** ve iş akışı Tasarımcısı yüzeyine bırakın.  
  
14. Sürükleme bir **Interop** etkinliğinden **geçiş** bölümünü **araç kutusu** sürükleyip **dizisi** etkinlik.  
  
15. Tıklayın **Interop** faaliyete **göz atmak için tıklatın...** Etiket, tip **DiscountCalculator** içinde **tür adı** ve'ı tıklatın **Tamam**.  
  
    > [!NOTE]
    >  Zaman <xref:System.Activities.Statements.Interop> etkinlik iş akışına eklenen ve `DiscountCalculator` türü olarak belirtilen kendi <xref:System.Activities.Statements.Interop.ActivityType%2A>, <xref:System.Activities.Statements.Interop> etkinliği gösteren üç <xref:System.Activities.ArgumentDirection.In> bağımsız değişkenleri ve üç <xref:System.Activities.ArgumentDirection.Out> temsil eden üç genel bağımsız değişkenleri özelliklerini `DiscountCalculator` etkinlik. <xref:System.Activities.ArgumentDirection.In> Bağımsız değişkenleri üç genel özellikleri ve üç aynı ada sahip <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenlere sahip aynı adlarla **kullanıma** özellik adına eklenir. Aşağıdaki adımlarda önceki adımlarda oluşturulan iş akışı bağımsız değişkenleri bağlı <xref:System.Activities.Statements.Interop> etkinliğin bağımsız değişkenler.  
  
16. Tür `DiscountPercent` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **DiscountPercentOut** özelliği ve SEKME tuşuna basın.  
  
17. Tür `Subtotal` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **Subtotal** özelliği ve SEKME tuşuna basın.  
  
18. Tür `Total` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **TotalOut** özelliği ve SEKME tuşuna basın.  
  
19. Sağ **Program.cs** içinde **Çözüm Gezgini** seçip **kodu görüntüle**.  
  
20. Aşağıdaki `using` deyimini dosyanın üst.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. Çağrı yorum `CalculateDiscountInCode` yönteminde `Main` yöntemi ve aşağıdaki kodu ekleyin.  
  
    > [!NOTE]
    >  Önceki yordamda ve varsayılan takip ettiğiniz değil, `Main` kodu varsa, içeriği değiştirin `Main` aşağıdaki kod ile.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. İçinde yeni bir yöntem oluşturma `Program` adlı sınıf `CalculateDiscountUsingDesignerWorkflow` , aşağıdaki kodu içerir.  
  
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
  
23. Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın. Farklı bir belirtmek için `Subtotal` tutar, değiştirin `SubtotalValue` aşağıdaki kodda.  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>Kuralları özelliklerine genel bakış  
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] Kurallar altyapısı kuralları İleri zincirleme desteğiyle önceliğe dayalı bir şekilde işlemek için destek sağlar. Kurallar, tek bir öğe veya bir koleksiyondaki öğelerin değerlendirilebilir. Kuralları ve belirli kurallar işlevler hakkında bilgi genel bakış için lütfen aşağıdaki tabloya bakın.  
  
|Kuralları özelliği|Belgeler|  
|-------------------|-------------------|  
|Kurallarına genel bakış|[Windows Workflow Foundation kurallar altyapısı giriş](https://go.microsoft.com/fwlink/?LinkID=152836)|  
|Kural kümesi|[İş akışlarında RuleSets kullanma](https://go.microsoft.com/fwlink/?LinkId=178516) ve <xref:System.Workflow.Activities.Rules.RuleSet>|  
|Değerlendirme kuralları|[RuleSets değerlendirme kuralları](https://go.microsoft.com/fwlink/?LinkId=178517)|  
|Zincirleme kuralları|[İleri denetim zincirleme](https://go.microsoft.com/fwlink/?LinkId=178518) ve [İleri kuralları zincirleme](https://go.microsoft.com/fwlink/?LinkId=178519)|  
|Kural koleksiyonlarında işleme|[Kural koleksiyonlarında işleme](https://go.microsoft.com/fwlink/?LinkId=178520)|  
|PolicyActivity kullanma|[PolicyActivity etkinliğini kullanarak](https://go.microsoft.com/fwlink/?LinkId=178521) ve <xref:System.Workflow.Activities.PolicyActivity>|  
  
 Oluşturulan iş akışları [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] tarafından sağlanan kuralları özelliklerin tümünü kullanmayan [!INCLUDE[wf1](../../../includes/wf1-md.md)]bildirim temelli etkinlik koşullar ve gibi koşullu etkinlikler gibi <xref:System.Workflow.Activities.ConditionedActivityGroup> ve <xref:System.Workflow.Activities.ReplicatorActivity>. Gerekirse, bu işlev kullanılarak oluşturulan iş akışları için kullanılabilir [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Daha fazla bilgi için [geçiş kılavuzuna](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).
