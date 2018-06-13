---
title: Özel Etkinlik özelliğinin bir tasarımcı denetimine bağlama
ms.date: 03/30/2017
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
ms.openlocfilehash: 1aa22403f5ed2de6893f8bfec9f03fa7dabd6868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513555"
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>Özel Etkinlik özelliğinin bir tasarımcı denetimine bağlama
Bir etkinlik bağımsız bir metin kutusu Tasarımcı denetimi bağlama oldukça basittir; bir etkinlik bağımsız değişkeni (örneğin, bir birleşik giriş kutusu) karmaşık bir Tasarımcı denetim bağlamayı, ancak zorluklara. Bu konu nasıl etkinlik bağımsız değişken özel etkinlik Tasarımcısı birleşik giriş kutusu denetiminde bağlanacağını açıklar.  
  
#### <a name="creating-the-combo-box-item-converter"></a>Birleşik giriş kutusu öğesi dönüştürücü oluşturma  
  
1.  Yeni bir boş çözüm CustomProperty adlı Visual Studio'da oluşturun.  
  
2.  ComboBoxItemConverter adlı yeni bir sınıf oluşturun. System.Windows.Data bir başvuru ekleyin ve türetilen sınıf sahip <xref:System.Windows.Data.IValueConverter>. Visual Studio için yer tutucular oluşturmak için arabirimi uygulayan sahip `Convert` ve `ConvertBack`.  
  
3.  Aşağıdaki kodu ekleyin `Convert` yöntemi. Bu kod etkinliğe ilişkin dönüştürür <xref:System.Activities.InArgument%601> türü <xref:System.String> Tasarımcısı'nda yerleştirilecek değer.  
  
    ```  
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
  
     Yukarıdaki kod parçacığında ifade kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> yerine <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
    ```  
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
  
4.  Aşağıdaki kodu ekleyin `ConvertBack` yöntemi. Gelen birleşik giriş kutusu öğesi yedeklemek için bu kodu dönüştürür bir <xref:System.Activities.InArgument%601>.  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     Yukarıdaki kod parçacığında ifade kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> yerine <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>Bir etkinlik özel Designer'a ComboBoxItemConverter ekleme  
  
1.  Yeni bir öğe projeye ekleyin. Yeni öğe iletişim kutusunda, iş akışı düğümünü seçin ve etkinlik Tasarımcısı yeni öğe türü olarak seçin. CustomPropertyDesigner öğesi adı.  
  
2.  Birleşik giriş kutusu yeni Designer'a ekleyin. Öğe özelliği "Item1" içerik değerlerle birleşik giriş kutusu öğeleri birkaç eklemek ve ' Item2 ".  
  
3.  Yeni öğe dönüştürücü açılan kutu için kullanılacak öğe dönüştürücü olarak eklemek için XAML açılan kutunun değiştirin. Dönüştürücü bir kaynak ActivityDesigner.Resources kesim olarak eklenir ve dönüştürücü dönüştürücü özniteliğini belirtir <xref:System.Windows.Controls.ComboBox>. Proje ad alanı için etkinlik Tasarımcısı ad alanları özniteliklerinde belirtilen unutmayın; Tasarımcı farklı bir projedeki kullanılacak ise, bu ad alanı değiştirilmesi gerekir.  
  
    ```  
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
  
4.  Yeni bir öğe türü oluşturmak <xref:System.Activities.CodeActivity>. IDE etkinliği tarafından oluşturulan varsayılan kod bu örnek için yeterli olacaktır.  
  
5.  Sınıf tanımına şu özniteliği ekleyin:  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     Bu satırı yeni designer yeni sınıfı ile ilişkilendirir.  
  
 Şimdi yeni etkinlik Tasarımcısı ile ilişkili olmalıdır. Yeni Etkinlik test etmek için bir iş akışına eklemek ve birleşik giriş kutusu iki değerleri ayarlayın. Özellikler penceresini birleşik giriş kutusu değeri yansıtacak şekilde güncelleştirmeniz gerekir.
