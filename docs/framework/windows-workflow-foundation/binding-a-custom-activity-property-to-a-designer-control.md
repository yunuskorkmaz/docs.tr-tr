---
title: Özel etkinlik özelliğini tasarımcı denetimine bağlama
ms.date: 03/30/2017
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
ms.openlocfilehash: 142a9eb273a98d3a2d83a1239d6d7c891d5cc305
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945905"
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>Özel etkinlik özelliğini tasarımcı denetimine bağlama

Bir etkinlik bağımsız değişkeni için bir metin kutusu Tasarımcı denetimine bağlama oldukça basittir; Etkinlik bağımsız değişkeni (örneğin, bir birleşik giriş kutusu) karmaşık Tasarımcı denetimine bağlama zorlukları, ancak sunabilir. Bu konuda, bir etkinlik bağımsız değişkeni bir birleşik giriş kutusu denetimi özel etkinlik tasarımcısında bağlamak anlatılmaktadır.

## <a name="creating-the-combo-box-item-converter"></a>Birleşik giriş kutusu öğesi dönüştürücü oluşturma

1. Visual Studio CustomProperty adlı yeni bir boş çözüm oluşturun.

2. ComboBoxItemConverter adlı yeni bir sınıf oluşturun. System.Windows.Data bir başvuru ekleyin ve türetilen sınıf sahip <xref:System.Windows.Data.IValueConverter>. Visual Studio için saplamalar oluşturmak için arabirimi gerçekleştirmeniz sahip `Convert` ve `ConvertBack`.

3. Aşağıdaki kodu ekleyin `Convert` yöntemi. Bu kod etkinliğin dönüştürür <xref:System.Activities.InArgument%601> türü <xref:System.String> Tasarımcısı'nda yerleştirilecek değer.

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

     Yukarıdaki kod parçacığında ifadesi kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> yerine <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.

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

4. Aşağıdaki kodu ekleyin `ConvertBack` yöntemi. Bu kod dönüştürür gelen birleşik giriş kutusu öğeyi yeniden bir <xref:System.Activities.InArgument%601>.

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(vbArgument);
                return inArgument;
    ```

     Yukarıdaki kod parçacığında ifadesi kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> yerine <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(csArgument);
                return inArgument;
    ```

## <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>Özel bir etkinlik Tasarımcısı için ComboBoxItemConverter ekleme

1. Yeni bir öğe projeye ekleyin. Yeni öğe iletişim kutusunda iş akışı düğümünü seçin ve etkinlik Tasarımcısı yeni öğe türü olarak seçin. ' % S'öğesi CustomPropertyDesigner adı.

2. Birleşik giriş kutusu yeni tasarımcıya ekleyin. Items özelliğini "Item1" içerik değerleriyle Kombo kutusu birkaç öğe ekleyin ve ' Item2 ".

3. Yeni öğe dönüştürücü için birleşik giriş kutusu kullanılacak öğe dönüştürücü olarak eklemek için kutunun XAML değiştirin. Dönüştürücü ActivityDesigner.Resources Segmentte bir kaynak olarak eklenir ve dönüştürücü dönüştürücü özniteliğini belirtir <xref:System.Windows.Controls.ComboBox>. Ad alanı projenin etkinlik Tasarımcısı için ad alanları özniteliklerinde belirtilen dikkat edin. Tasarımcı, farklı bir projede kullanılacak ise, bu ad alanı değiştirilmesi gerekir.

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

4. Yeni bir öğe türünün oluşturma <xref:System.Activities.CodeActivity>. IDE etkinliği tarafından oluşturulan varsayılan kod bu örnek için yeterli olacaktır.

5. Sınıf tanımına aşağıdaki özniteliği ekleyin:

    ```csharp
    [Designer(typeof(CustomPropertyDesigner))]
    ```

     Bu satır, yeni Tasarımcı yeni sınıf ile ilişkilendirir.

 Şimdi yeni etkinlik Tasarımcısı ile ilişkili olmalıdır. Yeni Etkinlik test etmek için bir iş akışına ekleme ve iki değerleri birleşik giriş kutusu ayarlayın. Özellikler penceresinde, birleşik giriş kutusu değeri yansıtacak şekilde güncelleştirmeniz gerekir.
