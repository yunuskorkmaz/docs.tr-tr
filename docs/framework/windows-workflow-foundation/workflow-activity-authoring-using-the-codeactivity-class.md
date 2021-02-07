---
description: 'Hakkında daha fazla bilgi edinin: CodeActivity sınıfını kullanarak Iş akışı etkinliği yazma'
title: CodeActivity sınıfını kullanarak iş akışı etkinlik yazma
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 393b6c586a88e876484f6888441d5bb82b4c0dad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754920"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>CodeActivity sınıfını kullanarak iş akışı etkinlik yazma

Devralma tarafından oluşturulan etkinlikler <xref:System.Activities.CodeActivity> , yöntemi geçersiz kılarak temel kesinlik davranışını uygulayabilir <xref:System.Activities.CodeActivity.Execute%2A> .

## <a name="using-codeactivitycontext"></a>CodeActivityContext kullanma

 İş akışı çalışma zamanının özelliklerine <xref:System.Activities.CodeActivity.Execute%2A> , türünün ' nin üyelerini kullanarak yönteminin içinden erişilebilir `context` <xref:System.Activities.CodeActivityContext> . Aracılığıyla kullanılabilen özellikler şunları <xref:System.Activities.CodeActivityContext> içerir:

- Değişkenlerin ve bağımsız değişkenlerin değerlerini alma ve ayarlama.

- Kullanarak özel izleme özellikleri <xref:System.Activities.CodeActivityContext.Track%2A> .

- Kullanılarak etkinliğin yürütme özelliklerine erişin <xref:System.Activities.CodeActivityContext.GetProperty%2A> .

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>CodeActivity 'den devralan özel etkinlik oluşturmak için

1. Visual Studio 2010 ' i açın.

2. **Dosya**, **Yeni** ve ardından **Proje**' yi seçin. **Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **etkinlik kitaplığı** ' nı seçin. Yeni proje Merhaba etkinliğini adlandırın.

3. Merhaba etkinlik projesinde Activity1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.

4. Merhaba etkinlik projesine sağ tıklayın ve **Ekle** ' yi ve ardından **sınıf**' ı seçin. Yeni sınıfı HelloActivity.cs olarak adlandırın.

5. HelloActivity.cs dosyasında aşağıdaki `using` yönergeleri ekleyin.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <xref:System.Activities.CodeActivity>Sınıf bildirimine bir temel sınıf ekleyerek yeni sınıfın öğesinden devralmasını sağlayın.

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. Bir yöntem ekleyerek sınıfa işlevsellik ekleyin <xref:System.Activities.CodeActivity.Execute%2A> .

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <xref:System.Activities.CodeActivityContext>İzleme kaydı oluşturmak için kullanın.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
