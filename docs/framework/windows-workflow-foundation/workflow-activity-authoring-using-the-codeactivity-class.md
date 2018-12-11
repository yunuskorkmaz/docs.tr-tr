---
title: CodeActivity sınıfını kullanarak iş akışı etkinliği yazma
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 4954dfa5dba03823d119a456149f0f16cf5ed410
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127101"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>CodeActivity sınıfını kullanarak iş akışı etkinliği yazma
Devralarak oluşturulan etkinlikleri <xref:System.Activities.CodeActivity> temel kesinlik temelli davranışını geçersiz kılarak uygulayabilirsiniz <xref:System.Activities.CodeActivity.Execute%2A> yöntemi.

## <a name="using-codeactivitycontext"></a>CodeActivityContext kullanma
 İş akışı çalışma zamanı özellikleri içinden erişilebilir <xref:System.Activities.CodeActivity.Execute%2A> üyeleri kullanarak yöntemi `context` türünde parametre <xref:System.Activities.CodeActivityContext>. Aracılığıyla kullanılabilen özellikleri <xref:System.Activities.CodeActivityContext> şunları içerir:

-   Alma ve değişkenleri ve bağımsız değişken değerlerini ayarlama.

-   Özel İzleme özelliklerini kullanarak <xref:System.Activities.CodeActivityContext.Track%2A>.

-   Kullanarak Etkinlik yürütme özelliklerine erişimi <xref:System.Activities.CodeActivityContext.GetProperty%2A>.

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>CodeActivity devralan bir özel etkinlik oluşturmak için

1.  Visual Studio 2010'u açın.

2.  Seçin **dosya**, **yeni**, ardından **proje**. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi. Yeni Proje HelloActivity adı.

3.  Gt;activity1.XAML HelloActivity projeye sağ tıklayıp **Sil**.

4.  HelloActivity projeye sağ tıklayıp **Ekle** , ardından **sınıfı**. Yeni bir sınıf HelloActivity.cs adı.

5.  HelloActivity.cs dosyasına aşağıdakileri ekleyin `using` yönergeleri.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6.  Devralınan yeni bir sınıf olun <xref:System.Activities.CodeActivity> için sınıf bildiriminin bir temel sınıf ekleyerek.

    ```csharp
    class HelloActivity : CodeActivity
    ```

7.  Ekleyerek sınıfına işlevsellik ekleme bir <xref:System.Activities.CodeActivity.Execute%2A> yöntemi.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8.  Kullanım <xref:System.Activities.CodeActivityContext> bir izleme kaydını oluşturmak için.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
