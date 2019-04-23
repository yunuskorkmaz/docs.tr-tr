---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimlerini BindingSource Bileşeni ile Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: a4f87303954494e8e32d32e68fb3f1244f25680a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304564"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="abfb4-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimlerini BindingSource Bileşeni ile Bağlama</span><span class="sxs-lookup"><span data-stu-id="abfb4-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="abfb4-103">Formunuza denetimler eklenir ve uygulamanız için kullanıcı arabirimi belirlenen sonra çalışma zamanında, kullanıcılar alter ve uygulamayla ilgili verileri kaydetme böylece bir veri kaynağına denetimlerin bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abfb4-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>  
  
 <span data-ttu-id="abfb4-104">Windows Forms'ta bir denetim veya denetimlerin bir dizisini bağlama en kolay gerçekleştirilir kullanarak <xref:System.Windows.Forms.BindingSource> denetimi form üzerinde denetimleri ve veri kaynağı arasında bir köprü olarak.</span><span class="sxs-lookup"><span data-stu-id="abfb4-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>  
  
 <span data-ttu-id="abfb4-105">Formdaki denetimlerin bir veya daha fazla veriye bağlı olabilir; Aşağıdaki yordamda bir <xref:System.Windows.Forms.TextBox> denetim bir veri kaynağına bağlı.</span><span class="sxs-lookup"><span data-stu-id="abfb4-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>  
  
 <span data-ttu-id="abfb4-106">Yordamı tamamlamak için bir veritabanından alınan veri kaynağına bağlayacaksınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="abfb4-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="abfb4-107">Diğer veri depolarından veri kaynakları oluşturma hakkında daha fazla bilgi için bkz. [yeni veri kaynağı ekleme](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="abfb4-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abfb4-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="abfb4-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="abfb4-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="abfb4-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="abfb4-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="abfb4-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="abfb4-111">Tasarım zamanında bir denetimi bağlamak için</span><span class="sxs-lookup"><span data-stu-id="abfb4-111">To bind a control at design time</span></span>  
  
1. <span data-ttu-id="abfb4-112">Sürükleme bir <xref:System.Windows.Forms.TextBox> denetim formu açın.</span><span class="sxs-lookup"><span data-stu-id="abfb4-112">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>  
  
2. <span data-ttu-id="abfb4-113">İçinde **özellikleri** penceresi:</span><span class="sxs-lookup"><span data-stu-id="abfb4-113">In the **Properties** window:</span></span>  
  
    1.  <span data-ttu-id="abfb4-114">Genişletin **(DataBindings)** düğümü.</span><span class="sxs-lookup"><span data-stu-id="abfb4-114">Expand the **(DataBindings)** node.</span></span>  
  
    2.  <span data-ttu-id="abfb4-115">Yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="abfb4-115">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
         <span data-ttu-id="abfb4-116">**DataSource** UI türü Düzenleyici açar.</span><span class="sxs-lookup"><span data-stu-id="abfb4-116">The **DataSource** UI type editor opens.</span></span>  
  
         <span data-ttu-id="abfb4-117">Bir veri kaynağı, daha önce proje veya form için yapılandırıldı, görünür.</span><span class="sxs-lookup"><span data-stu-id="abfb4-117">If a data source has previously been configured for the project or form, it will appear.</span></span>  
  
3. <span data-ttu-id="abfb4-118">Tıklayın **proje veri kaynağı Ekle** verilere bağlanmak ve bir veri kaynağı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="abfb4-118">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
4. <span data-ttu-id="abfb4-119">Üzerinde **veri kaynağı Yapılandırma Sihirbazı** Karşılama sayfasında, tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="abfb4-119">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
5. <span data-ttu-id="abfb4-120">Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı**.</span><span class="sxs-lookup"><span data-stu-id="abfb4-120">On the **Choose a Data Source Type** page, select **Database**.</span></span>  
  
6. <span data-ttu-id="abfb4-121">Üzerinde **veri bağlantınızı seçin** sayfasında, kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin.</span><span class="sxs-lookup"><span data-stu-id="abfb4-121">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="abfb4-122">İstenen veri bağlantınızı seçin kullanılabilir değilse **yeni bağlantı** yeni bir veri bağlantısı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="abfb4-122">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>  
  
7. <span data-ttu-id="abfb4-123">Seçin **Evet, bağlantıyı Kaydet** bağlantı dizesini uygulama yapılandırma dosyasına kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="abfb4-123">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
8. <span data-ttu-id="abfb4-124">Uygulamanıza getirmek için veritabanı nesneleri seçin.</span><span class="sxs-lookup"><span data-stu-id="abfb4-124">Select the database objects to bring into your application.</span></span> <span data-ttu-id="abfb4-125">Bu durumda, istediğiniz bir tabloda bir alan seçin <xref:System.Windows.Forms.TextBox> görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="abfb4-125">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>  
  
9. <span data-ttu-id="abfb4-126">İsterseniz varsayılan veri kümesi adı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="abfb4-126">Replace the default dataset name if you want.</span></span>  
  
10. <span data-ttu-id="abfb4-127">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="abfb4-127">Click **Finish**.</span></span>  
  
11. <span data-ttu-id="abfb4-128">İçinde **özellikleri** penceresinde yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> yeniden özelliği.</span><span class="sxs-lookup"><span data-stu-id="abfb4-128">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="abfb4-129">İçinde **DataSource** UI türü Düzenleyici bağlamak için alan adı seçin <xref:System.Windows.Forms.TextBox> için.</span><span class="sxs-lookup"><span data-stu-id="abfb4-129">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>  
  
     <span data-ttu-id="abfb4-130">**DataSource** UI türü Düzenleyici kapanır ve veri kümesi <xref:System.Windows.Forms.BindingSource> ve tablo bağdaştırıcısı belirli veri bağlantısı formunuza eklenir.</span><span class="sxs-lookup"><span data-stu-id="abfb4-130">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abfb4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abfb4-131">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="abfb4-132">Yeni veri kaynağı ekleme</span><span class="sxs-lookup"><span data-stu-id="abfb4-132">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- <span data-ttu-id="abfb4-133">[Veri kaynakları penceresi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="abfb4-133">[Data Sources Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span></span>