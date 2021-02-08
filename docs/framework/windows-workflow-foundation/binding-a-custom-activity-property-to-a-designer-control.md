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
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="1bd54-103">Özel etkinlik özelliğini tasarımcı denetimine bağlama</span><span class="sxs-lookup"><span data-stu-id="1bd54-103">Binding a custom activity property to a designer control</span></span>

<span data-ttu-id="1bd54-104">Bir metin kutusu Tasarımcı denetimini bir etkinlik bağımsız değişkenine bağlama oldukça basittir; bir etkinlik bağımsız değişkenine karmaşık tasarımcı denetiminin (örneğin, Birleşik giriş kutusu) bağlanması, sorunlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="1bd54-104">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="1bd54-105">Bu konuda, bir etkinlik bağımsız değişkeninin özel bir etkinlik tasarımcısında bir açılan kutu denetimine nasıl bağlanacağı anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bd54-105">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>

## <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="1bd54-106">Birleşik giriş kutusu öğe dönüştürücüsünü oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bd54-106">Creating the combo box item converter</span></span>

1. <span data-ttu-id="1bd54-107">Visual Studio 'da CustomProperty adlı yeni bir boş çözüm oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bd54-107">Create a new empty solution in Visual Studio called CustomProperty.</span></span>

2. <span data-ttu-id="1bd54-108">ComboBoxItemConverter adlı yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bd54-108">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="1bd54-109">System. Windows. Data öğesine bir başvuru ekleyin ve sınıfın türemesini sağlayabilirsiniz <xref:System.Windows.Data.IValueConverter> .</span><span class="sxs-lookup"><span data-stu-id="1bd54-109">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="1bd54-110">Visual Studio 'nun ve için saplamalar oluşturmak üzere arabirimini uygulaması gerekir `Convert` `ConvertBack` .</span><span class="sxs-lookup"><span data-stu-id="1bd54-110">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>

3. <span data-ttu-id="1bd54-111">`Convert` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd54-111">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="1bd54-112">Bu kod, etkinliğin <xref:System.Activities.InArgument%601> türünü <xref:System.String> tasarımcıya yerleştirilecek değere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1bd54-112">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>

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

     <span data-ttu-id="1bd54-113">Yukarıdaki kod parçacığında ifadesi yerine kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> .</span><span class="sxs-lookup"><span data-stu-id="1bd54-113">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>

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

4. <span data-ttu-id="1bd54-114">`ConvertBack` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd54-114">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="1bd54-115">Bu kod, gelen Birleşik giriş kutusu öğesini geri dönüştürür <xref:System.Activities.InArgument%601> .</span><span class="sxs-lookup"><span data-stu-id="1bd54-115">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(vbArgument);
                return inArgument;
    ```

     <span data-ttu-id="1bd54-116">Yukarıdaki kod parçacığında ifadesi yerine kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> .</span><span class="sxs-lookup"><span data-stu-id="1bd54-116">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(csArgument);
                return inArgument;
    ```

## <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="1bd54-117">Bir etkinliğin özel tasarımcısına ComboBoxItemConverter ekleme</span><span class="sxs-lookup"><span data-stu-id="1bd54-117">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>

1. <span data-ttu-id="1bd54-118">Projeye yeni bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd54-118">Add a new item to the project.</span></span> <span data-ttu-id="1bd54-119">Yeni öğe iletişim kutusunda Iş akışı düğümünü seçin ve yeni öğe türü olarak etkinlik Tasarımcısı ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="1bd54-119">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="1bd54-120">Öğeyi CustomPropertyDesigner olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1bd54-120">Name the item CustomPropertyDesigner.</span></span>

2. <span data-ttu-id="1bd54-121">Yeni tasarımcıya Birleşik giriş kutusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd54-121">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="1bd54-122">Items özelliğinde, "Item1" ve "Item2" Içerik değerleriyle birlikte Birleşik giriş kutusuna birkaç öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd54-122">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>

3. <span data-ttu-id="1bd54-123">Birleşik giriş kutusu için kullanılacak öğe dönüştürücü olarak yeni öğe dönüştürücüsünü eklemek için açılan kutunun XAML 'sini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1bd54-123">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="1bd54-124">Dönüştürücü, ActivityDesigner. resources segmentine bir kaynak olarak eklenir ve için dönüştürücü özniteliğinde dönüştürücüyü belirtir <xref:System.Windows.Controls.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="1bd54-124">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="1bd54-125">Projenin ad alanının, etkinlik Tasarımcısı için ad alanları özniteliklerinde belirtildiğine unutmayın; Tasarımcı farklı bir projede kullanılacaksa, bu ad alanının değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bd54-125">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>

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

4. <span data-ttu-id="1bd54-126">Türünde yeni bir öğe oluşturun <xref:System.Activities.CodeActivity> .</span><span class="sxs-lookup"><span data-stu-id="1bd54-126">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="1bd54-127">Etkinlik için IDE tarafından oluşturulan varsayılan kod bu örnek için yeterli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1bd54-127">The default code created by the IDE for the activity will be sufficient for this example.</span></span>

5. <span data-ttu-id="1bd54-128">Aşağıdaki özniteliği sınıf tanımına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1bd54-128">Add the following attribute to the class definition:</span></span>

    ```csharp
    [Designer(typeof(CustomPropertyDesigner))]
    ```

     <span data-ttu-id="1bd54-129">Bu satır yeni tasarımcıyı yeni sınıfla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="1bd54-129">This line associates the new designer with the new class.</span></span>

 <span data-ttu-id="1bd54-130">Yeni etkinlik artık tasarımcı ile ilişkilendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="1bd54-130">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="1bd54-131">Yeni etkinliği test etmek için bir iş akışına ekleyin ve Birleşik giriş kutusunu iki değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1bd54-131">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="1bd54-132">Özellikler penceresi, Birleşik giriş kutusu değerini yansıtacak şekilde güncellemelidir.</span><span class="sxs-lookup"><span data-stu-id="1bd54-132">The properties window should update to reflect the combo box value.</span></span>
