---
title: "Özel Etkinlik özelliğinin bir tasarımcı denetimine bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 07a39983d0e561fdad4c09e641912b0d15aa4033
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="d56bd-102">Özel Etkinlik özelliğinin bir tasarımcı denetimine bağlama</span><span class="sxs-lookup"><span data-stu-id="d56bd-102">Binding a custom activity property to a designer control</span></span>
<span data-ttu-id="d56bd-103">Bir etkinlik bağımsız bir metin kutusu Tasarımcı denetimi bağlama oldukça basittir; bir etkinlik bağımsız değişkeni (örneğin, bir birleşik giriş kutusu) karmaşık bir Tasarımcı denetim bağlamayı, ancak zorluklara.</span><span class="sxs-lookup"><span data-stu-id="d56bd-103">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="d56bd-104">Bu konu nasıl etkinlik bağımsız değişken özel etkinlik Tasarımcısı birleşik giriş kutusu denetiminde bağlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d56bd-104">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>  
  
#### <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="d56bd-105">Birleşik giriş kutusu öğesi dönüştürücü oluşturma</span><span class="sxs-lookup"><span data-stu-id="d56bd-105">Creating the combo box item converter</span></span>  
  
1.  <span data-ttu-id="d56bd-106">Yeni bir boş çözüm CustomProperty adlı Visual Studio'da oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d56bd-106">Create a new empty solution in Visual Studio called CustomProperty.</span></span>  
  
2.  <span data-ttu-id="d56bd-107">ComboBoxItemConverter adlı yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d56bd-107">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="d56bd-108">System.Windows.Data bir başvuru ekleyin ve türetilen sınıf sahip <xref:System.Windows.Data.IValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="d56bd-108">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="d56bd-109">Visual Studio için yer tutucular oluşturmak için arabirimi uygulayan sahip `Convert` ve `ConvertBack`.</span><span class="sxs-lookup"><span data-stu-id="d56bd-109">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>  
  
3.  <span data-ttu-id="d56bd-110">Aşağıdaki kodu ekleyin `Convert` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d56bd-110">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="d56bd-111">Bu kod etkinliğe ilişkin dönüştürür <xref:System.Activities.InArgument%601> türü <xref:System.String> Tasarımcısı'nda yerleştirilecek değer.</span><span class="sxs-lookup"><span data-stu-id="d56bd-111">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>  
  
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
  
     <span data-ttu-id="d56bd-112">Yukarıdaki kod parçacığında ifade kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> yerine <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="d56bd-112">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
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
  
4.  <span data-ttu-id="d56bd-113">Aşağıdaki kodu ekleyin `ConvertBack` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d56bd-113">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="d56bd-114">Gelen birleşik giriş kutusu öğesi yedeklemek için bu kodu dönüştürür bir <xref:System.Activities.InArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="d56bd-114">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     <span data-ttu-id="d56bd-115">Yukarıdaki kod parçacığında ifade kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> yerine <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="d56bd-115">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="d56bd-116">Bir etkinlik özel Designer'a ComboBoxItemConverter ekleme</span><span class="sxs-lookup"><span data-stu-id="d56bd-116">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>  
  
1.  <span data-ttu-id="d56bd-117">Yeni bir öğe projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d56bd-117">Add a new item to the project.</span></span> <span data-ttu-id="d56bd-118">Yeni öğe iletişim kutusunda, iş akışı düğümünü seçin ve etkinlik Tasarımcısı yeni öğe türü olarak seçin.</span><span class="sxs-lookup"><span data-stu-id="d56bd-118">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="d56bd-119">CustomPropertyDesigner öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="d56bd-119">Name the item CustomPropertyDesigner.</span></span>  
  
2.  <span data-ttu-id="d56bd-120">Birleşik giriş kutusu yeni Designer'a ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d56bd-120">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="d56bd-121">Öğe özelliği "Item1" içerik değerlerle birleşik giriş kutusu öğeleri birkaç eklemek ve ' Item2 ".</span><span class="sxs-lookup"><span data-stu-id="d56bd-121">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>  
  
3.  <span data-ttu-id="d56bd-122">Yeni öğe dönüştürücü açılan kutu için kullanılacak öğe dönüştürücü olarak eklemek için XAML açılan kutunun değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d56bd-122">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="d56bd-123">Dönüştürücü bir kaynak ActivityDesigner.Resources kesim olarak eklenir ve dönüştürücü dönüştürücü özniteliğini belirtir <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="d56bd-123">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="d56bd-124">Proje ad alanı için etkinlik Tasarımcısı ad alanları özniteliklerinde belirtilen unutmayın; Tasarımcı farklı bir projedeki kullanılacak ise, bu ad alanı değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d56bd-124">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>  
  
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
  
4.  <span data-ttu-id="d56bd-125">Yeni bir öğe türü oluşturmak <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="d56bd-125">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="d56bd-126">IDE etkinliği tarafından oluşturulan varsayılan kod bu örnek için yeterli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d56bd-126">The default code created by the IDE for the activity will be sufficient for this example.</span></span>  
  
5.  <span data-ttu-id="d56bd-127">Sınıf tanımına şu özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d56bd-127">Add the following attribute to the class definition:</span></span>  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     <span data-ttu-id="d56bd-128">Bu satırı yeni designer yeni sınıfı ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d56bd-128">This line associates the new designer with the new class.</span></span>  
  
 <span data-ttu-id="d56bd-129">Şimdi yeni etkinlik Tasarımcısı ile ilişkili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d56bd-129">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="d56bd-130">Yeni Etkinlik test etmek için bir iş akışına eklemek ve birleşik giriş kutusu iki değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d56bd-130">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="d56bd-131">Özellikler penceresini birleşik giriş kutusu değeri yansıtacak şekilde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d56bd-131">The properties window should update to reflect the combo box value.</span></span>
