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
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="c4b78-102">Özel etkinlik özelliğini tasarımcı denetimine bağlama</span><span class="sxs-lookup"><span data-stu-id="c4b78-102">Binding a custom activity property to a designer control</span></span>

<span data-ttu-id="c4b78-103">Bir etkinlik bağımsız değişkeni için bir metin kutusu Tasarımcı denetimine bağlama oldukça basittir; Etkinlik bağımsız değişkeni (örneğin, bir birleşik giriş kutusu) karmaşık Tasarımcı denetimine bağlama zorlukları, ancak sunabilir.</span><span class="sxs-lookup"><span data-stu-id="c4b78-103">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="c4b78-104">Bu konuda, bir etkinlik bağımsız değişkeni bir birleşik giriş kutusu denetimi özel etkinlik tasarımcısında bağlamak anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4b78-104">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>

## <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="c4b78-105">Birleşik giriş kutusu öğesi dönüştürücü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4b78-105">Creating the combo box item converter</span></span>

1. <span data-ttu-id="c4b78-106">Visual Studio CustomProperty adlı yeni bir boş çözüm oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4b78-106">Create a new empty solution in Visual Studio called CustomProperty.</span></span>

2. <span data-ttu-id="c4b78-107">ComboBoxItemConverter adlı yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4b78-107">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="c4b78-108">System.Windows.Data bir başvuru ekleyin ve türetilen sınıf sahip <xref:System.Windows.Data.IValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="c4b78-108">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="c4b78-109">Visual Studio için saplamalar oluşturmak için arabirimi gerçekleştirmeniz sahip `Convert` ve `ConvertBack`.</span><span class="sxs-lookup"><span data-stu-id="c4b78-109">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>

3. <span data-ttu-id="c4b78-110">Aşağıdaki kodu ekleyin `Convert` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c4b78-110">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="c4b78-111">Bu kod etkinliğin dönüştürür <xref:System.Activities.InArgument%601> türü <xref:System.String> Tasarımcısı'nda yerleştirilecek değer.</span><span class="sxs-lookup"><span data-stu-id="c4b78-111">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>

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

     <span data-ttu-id="c4b78-112">Yukarıdaki kod parçacığında ifadesi kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> yerine <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="c4b78-112">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>

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

4. <span data-ttu-id="c4b78-113">Aşağıdaki kodu ekleyin `ConvertBack` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c4b78-113">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="c4b78-114">Bu kod dönüştürür gelen birleşik giriş kutusu öğeyi yeniden bir <xref:System.Activities.InArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="c4b78-114">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(vbArgument);
                return inArgument;
    ```

     <span data-ttu-id="c4b78-115">Yukarıdaki kod parçacığında ifadesi kullanılarak da oluşturulabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> yerine <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="c4b78-115">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(csArgument);
                return inArgument;
    ```

## <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="c4b78-116">Özel bir etkinlik Tasarımcısı için ComboBoxItemConverter ekleme</span><span class="sxs-lookup"><span data-stu-id="c4b78-116">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>

1. <span data-ttu-id="c4b78-117">Yeni bir öğe projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c4b78-117">Add a new item to the project.</span></span> <span data-ttu-id="c4b78-118">Yeni öğe iletişim kutusunda iş akışı düğümünü seçin ve etkinlik Tasarımcısı yeni öğe türü olarak seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b78-118">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="c4b78-119">' % S'öğesi CustomPropertyDesigner adı.</span><span class="sxs-lookup"><span data-stu-id="c4b78-119">Name the item CustomPropertyDesigner.</span></span>

2. <span data-ttu-id="c4b78-120">Birleşik giriş kutusu yeni tasarımcıya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c4b78-120">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="c4b78-121">Items özelliğini "Item1" içerik değerleriyle Kombo kutusu birkaç öğe ekleyin ve ' Item2 ".</span><span class="sxs-lookup"><span data-stu-id="c4b78-121">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>

3. <span data-ttu-id="c4b78-122">Yeni öğe dönüştürücü için birleşik giriş kutusu kullanılacak öğe dönüştürücü olarak eklemek için kutunun XAML değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c4b78-122">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="c4b78-123">Dönüştürücü ActivityDesigner.Resources Segmentte bir kaynak olarak eklenir ve dönüştürücü dönüştürücü özniteliğini belirtir <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="c4b78-123">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="c4b78-124">Ad alanı projenin etkinlik Tasarımcısı için ad alanları özniteliklerinde belirtilen dikkat edin. Tasarımcı, farklı bir projede kullanılacak ise, bu ad alanı değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4b78-124">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>

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

4. <span data-ttu-id="c4b78-125">Yeni bir öğe türünün oluşturma <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="c4b78-125">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="c4b78-126">IDE etkinliği tarafından oluşturulan varsayılan kod bu örnek için yeterli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c4b78-126">The default code created by the IDE for the activity will be sufficient for this example.</span></span>

5. <span data-ttu-id="c4b78-127">Sınıf tanımına aşağıdaki özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c4b78-127">Add the following attribute to the class definition:</span></span>

    ```csharp
    [Designer(typeof(CustomPropertyDesigner))]
    ```

     <span data-ttu-id="c4b78-128">Bu satır, yeni Tasarımcı yeni sınıf ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="c4b78-128">This line associates the new designer with the new class.</span></span>

 <span data-ttu-id="c4b78-129">Şimdi yeni etkinlik Tasarımcısı ile ilişkili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4b78-129">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="c4b78-130">Yeni Etkinlik test etmek için bir iş akışına ekleme ve iki değerleri birleşik giriş kutusu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c4b78-130">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="c4b78-131">Özellikler penceresinde, birleşik giriş kutusu değeri yansıtacak şekilde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4b78-131">The properties window should update to reflect the combo box value.</span></span>
