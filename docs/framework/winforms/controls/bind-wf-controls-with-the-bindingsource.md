---
title: Tasarımcıyı kullanarak BindingSource bileşeniyle denetimleri bağlama
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 35b3fb7b9884f07dd6e2aef311a01d3090c44227
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744383"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="c2032-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimlerini BindingSource Bileşeni ile Bağlama</span><span class="sxs-lookup"><span data-stu-id="c2032-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="c2032-103">Formunuza denetimler ekledikten ve uygulamanız için Kullanıcı arabirimini belirledikten sonra, denetimleri bir veri kaynağına bağlayabilirsiniz, böylece çalışma zamanında kullanıcılar uygulamayla ilgili verileri değiştirebilir ve kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="c2032-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>

 <span data-ttu-id="c2032-104">Windows Forms denetimleri veya denetim dizilerini, form ve veri kaynağındaki denetimler arasında bir köprü olarak <xref:System.Windows.Forms.BindingSource> denetimi kullanılarak kolayca gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c2032-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>

 <span data-ttu-id="c2032-105">Form üzerindeki bir veya daha fazla denetim verilere bağlanabilir; Aşağıdaki yordamda, bir <xref:System.Windows.Forms.TextBox> denetimi bir veri kaynağına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="c2032-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>

 <span data-ttu-id="c2032-106">Yordamı gerçekleştirmek için bir veritabanından türetilmiş bir veri kaynağına bağlayacağınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c2032-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="c2032-107">Diğer veri mağazalarından veri kaynakları oluşturma hakkında daha fazla bilgi için bkz. [Yeni veri kaynakları ekleme](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="c2032-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>

## <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="c2032-108">Tasarım zamanında bir denetimi bağlamak için</span><span class="sxs-lookup"><span data-stu-id="c2032-108">To bind a control at design time</span></span>

1. <span data-ttu-id="c2032-109">Bir <xref:System.Windows.Forms.TextBox> denetimini forma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c2032-109">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>

2. <span data-ttu-id="c2032-110">**Özellikler** penceresinde:</span><span class="sxs-lookup"><span data-stu-id="c2032-110">In the **Properties** window:</span></span>

    1. <span data-ttu-id="c2032-111">**(DataBindings)** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="c2032-111">Expand the **(DataBindings)** node.</span></span>

    2. <span data-ttu-id="c2032-112"><xref:System.Windows.Forms.TextBox.Text%2A> özelliğinin yanındaki oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2032-112">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

         <span data-ttu-id="c2032-113">**DataSource** Kullanıcı arabirimi tür Düzenleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="c2032-113">The **DataSource** UI type editor opens.</span></span>

         <span data-ttu-id="c2032-114">Bir veri kaynağı daha önce proje veya form için yapılandırıldıysa, görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c2032-114">If a data source has previously been configured for the project or form, it will appear.</span></span>

3. <span data-ttu-id="c2032-115">Verilere bağlanmak ve bir veri kaynağı oluşturmak için **proje veri kaynağı Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2032-115">Click **Add Project Data Source** to connect to data and create a data source.</span></span>

4. <span data-ttu-id="c2032-116">**Veri kaynağı Yapılandırma Sihirbazı** 'na hoş geldiniz sayfasında **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2032-116">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>

5. <span data-ttu-id="c2032-117">**Veri kaynağı türü seç** sayfasında, **veritabanı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="c2032-117">On the **Choose a Data Source Type** page, select **Database**.</span></span>

6. <span data-ttu-id="c2032-118">**Veri bağlantınızı seçin** sayfasında, kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin.</span><span class="sxs-lookup"><span data-stu-id="c2032-118">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="c2032-119">İstediğiniz veri bağlantınız yoksa yeni bir veri bağlantısı oluşturmak için **Yeni bağlantı** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c2032-119">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>

7. <span data-ttu-id="c2032-120">**Evet ' i seçin,** bağlantı dizesini uygulama yapılandırma dosyasına kaydetmek için bağlantıyı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c2032-120">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>

8. <span data-ttu-id="c2032-121">Uygulamanıza getirmek istediğiniz veritabanı nesnelerini seçin.</span><span class="sxs-lookup"><span data-stu-id="c2032-121">Select the database objects to bring into your application.</span></span> <span data-ttu-id="c2032-122">Bu durumda, <xref:System.Windows.Forms.TextBox> görüntülenmesini istediğiniz tablodaki bir alanı seçin.</span><span class="sxs-lookup"><span data-stu-id="c2032-122">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>

9. <span data-ttu-id="c2032-123">İsterseniz varsayılan veri kümesi adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c2032-123">Replace the default dataset name if you want.</span></span>

10. <span data-ttu-id="c2032-124">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2032-124">Click **Finish**.</span></span>

11. <span data-ttu-id="c2032-125">**Özellikler** penceresinde, <xref:System.Windows.Forms.TextBox.Text%2A> özelliğinin yanındaki oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2032-125">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="c2032-126">**DataSource** Kullanıcı arabirimi türü düzenleyicisinde, <xref:System.Windows.Forms.TextBox> bağlanacağı alanın adını seçin.</span><span class="sxs-lookup"><span data-stu-id="c2032-126">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>

     <span data-ttu-id="c2032-127">**DataSource** Kullanıcı arabirimi tür Düzenleyicisi kapanır ve bu veri bağlantısına özgü veri kümesi, <xref:System.Windows.Forms.BindingSource> ve tablo bağdaştırıcısı formunuza eklenir.</span><span class="sxs-lookup"><span data-stu-id="c2032-127">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2032-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2032-128">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="c2032-129">Yeni veri kaynağı ekleme</span><span class="sxs-lookup"><span data-stu-id="c2032-129">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- <span data-ttu-id="c2032-130">[Veri kaynakları penceresi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c2032-130">[Data Sources Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span></span>
