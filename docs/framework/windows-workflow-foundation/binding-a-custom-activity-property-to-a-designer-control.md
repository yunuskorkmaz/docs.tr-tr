---
description: 'Daha fazla bilgi edinin: özel etkinlik özelliğini Tasarımcı denetimine bağlama'
title: Özel etkinlik özelliğini tasarımcı denetimine bağlama
ms.date: 03/30/2017
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
ms.openlocfilehash: 522e3df3028270d42f7654026383c628ec951e8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787948"
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>Özel etkinlik özelliğini tasarımcı denetimine bağlama

Bir metin kutusu Tasarımcı denetimini bir etkinlik bağımsız değişkenine bağlama oldukça basittir; bir etkinlik bağımsız değişkenine karmaşık tasarımcı denetiminin (örneğin, Birleşik giriş kutusu) bağlanması, sorunlar oluşturabilir. Bu konuda, bir etkinlik bağımsız değişkeninin özel bir etkinlik tasarımcısında bir açılan kutu denetimine nasıl bağlanacağı anlatılmaktadır.

## <a name="creating-the-combo-box-item-converter"></a>Birleşik giriş kutusu öğe dönüştürücüsünü oluşturma

1. Visual Studio 'da CustomProperty adlı yeni bir boş çözüm oluşturun.

2. ComboBoxItemConverter adlı yeni bir sınıf oluşturun. System. Windows. Data öğesine bir başvuru ekleyin ve sınıfın türemesini sağlayabilirsiniz <xref:System.Windows.Data.IValueConverter> . Visual Studio 'nun ve için saplamalar oluşturmak üzere arabirimini uygulaması gerekir `Convert` `ConvertBack` .

3. `Convert` yöntemine aşağıdaki kodu ekleyin. Bu kod, etkinliğin <xref:System.Activities.InArgument%601> türünü <xref:System.String> tasarımcıya yerleştirilecek değere dönüştürür.

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            VisualBasicValue<string> vbexpression = expression as VisualBasicValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (vbexpression != null)
            {
                return vbexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

     Yukarıdaki kod parçacığında ifadesi yerine kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> .

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            CSharpValue<string> csexpression = expression as CSharpValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (csexpression != null)
            {
                return csexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

4. `ConvertBack` yöntemine aşağıdaki kodu ekleyin. Bu kod, gelen Birleşik giriş kutusu öğesini geri dönüştürür <xref:System.Activities.InArgument%601> .

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(vbArgument);
                return inArgument;
    ```

     Yukarıdaki kod parçacığında ifadesi yerine kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> .

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(csArgument);
                return inArgument;
    ```

## <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>Bir etkinliğin özel tasarımcısına ComboBoxItemConverter ekleme

1. Projeye yeni bir öğe ekleyin. Yeni öğe iletişim kutusunda Iş akışı düğümünü seçin ve yeni öğe türü olarak etkinlik Tasarımcısı ' nı seçin. Öğeyi CustomPropertyDesigner olarak adlandırın.

2. Yeni tasarımcıya Birleşik giriş kutusu ekleyin. Items özelliğinde, "Item1" ve "Item2" Içerik değerleriyle birlikte Birleşik giriş kutusuna birkaç öğe ekleyin.

3. Birleşik giriş kutusu için kullanılacak öğe dönüştürücü olarak yeni öğe dönüştürücüsünü eklemek için açılan kutunun XAML 'sini değiştirin. Dönüştürücü, ActivityDesigner. resources segmentine bir kaynak olarak eklenir ve için dönüştürücü özniteliğinde dönüştürücüyü belirtir <xref:System.Windows.Controls.ComboBox> . Projenin ad alanının, etkinlik Tasarımcısı için ad alanları özniteliklerinde belirtildiğine unutmayın; Tasarımcı farklı bir projede kullanılacaksa, bu ad alanının değiştirilmesi gerekir.

    ```xaml
    <sap:ActivityDesigner x:Class="CustomProperty.CustomPropertyDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:c="clr-namespace:CustomProperty"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">

        <sap:ActivityDesigner.Resources>
            <ResourceDictionary>
                <c:ComboBoxItemConverter x:Key="comboBoxItemConverter"/>
            </ResourceDictionary>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ComboBox SelectedValue="{Binding Path=ModelItem.Text, Mode=TwoWay, Converter={StaticResource comboBoxItemConverter}}"  Height="23" HorizontalAlignment="Left" Margin="132,5,0,0" Name="comboBox1" VerticalAlignment="Top" Width="120" ItemsSource="{Binding}">
                <ComboBoxItem>item1</ComboBoxItem>
                <ComboBoxItem>item2</ComboBoxItem>
            </ComboBox>
        </Grid>
    </sap:ActivityDesigner>
    ```

4. Türünde yeni bir öğe oluşturun <xref:System.Activities.CodeActivity> . Etkinlik için IDE tarafından oluşturulan varsayılan kod bu örnek için yeterli olacaktır.

5. Aşağıdaki özniteliği sınıf tanımına ekleyin:

    ```csharp
    [Designer(typeof(CustomPropertyDesigner))]
    ```

     Bu satır yeni tasarımcıyı yeni sınıfla ilişkilendirir.

 Yeni etkinlik artık tasarımcı ile ilişkilendirilmelidir. Yeni etkinliği test etmek için bir iş akışına ekleyin ve Birleşik giriş kutusunu iki değere ayarlayın. Özellikler penceresi, Birleşik giriş kutusu değerini yansıtacak şekilde güncellemelidir.
