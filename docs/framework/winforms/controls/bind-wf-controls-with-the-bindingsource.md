---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimlerini BindingSource Bileşeni ile Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 3acbd17e8e969bb448e6deaf17dec23e44fa3bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527569"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="2a70b-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimlerini BindingSource Bileşeni ile Bağlama</span><span class="sxs-lookup"><span data-stu-id="2a70b-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="2a70b-103">Formunuza denetimler eklenir ve uygulamanız için kullanıcı arabirimi belirlenen sonra çalışma zamanında, kullanıcılar alter ve uygulamayla ilgili verileri kaydetmek böylece bir veri kaynağına denetimlerini bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a70b-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>  
  
 <span data-ttu-id="2a70b-104">Windows Forms'ta denetim veya denetimlerin bir dizi bağlama en kolay gerçekleştirilir kullanarak <xref:System.Windows.Forms.BindingSource> denetim form üzerinde denetimleri ve veri kaynağı arasında bir köprü olarak.</span><span class="sxs-lookup"><span data-stu-id="2a70b-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>  
  
 <span data-ttu-id="2a70b-105">Bir form üzerinde bir veya daha fazla denetimler veriye bağlı olabilir; Aşağıdaki yordamda bir <xref:System.Windows.Forms.TextBox> denetim bir veri kaynağına bağlı.</span><span class="sxs-lookup"><span data-stu-id="2a70b-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>  
  
 <span data-ttu-id="2a70b-106">Yordamı tamamlamak için bir veritabanından türetilmiş bir veri kaynağına bağlı olacağı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="2a70b-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="2a70b-107">Diğer veri depoları veri kaynakları oluşturma hakkında daha fazla bilgi için bkz: [yeni veri kaynakları ekleyin](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="2a70b-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a70b-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2a70b-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2a70b-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="2a70b-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2a70b-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="2a70b-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="2a70b-111">Tasarım zamanında denetim bağlamak için</span><span class="sxs-lookup"><span data-stu-id="2a70b-111">To bind a control at design time</span></span>  
  
1.  <span data-ttu-id="2a70b-112">Sürükleme bir <xref:System.Windows.Forms.TextBox> denetim form açın.</span><span class="sxs-lookup"><span data-stu-id="2a70b-112">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>  
  
2.  <span data-ttu-id="2a70b-113">İçinde **özellikleri** penceresi:</span><span class="sxs-lookup"><span data-stu-id="2a70b-113">In the **Properties** window:</span></span>  
  
    1.  <span data-ttu-id="2a70b-114">Genişletme **(veri bağlamaları)** düğümü.</span><span class="sxs-lookup"><span data-stu-id="2a70b-114">Expand the **(DataBindings)** node.</span></span>  
  
    2.  <span data-ttu-id="2a70b-115">Yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2a70b-115">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
         <span data-ttu-id="2a70b-116">**DataSource** UI türü Düzenleyici açar.</span><span class="sxs-lookup"><span data-stu-id="2a70b-116">The **DataSource** UI type editor opens.</span></span>  
  
         <span data-ttu-id="2a70b-117">Bir veri kaynağı, daha önce proje veya form için yapılandırılmışsa, görünür.</span><span class="sxs-lookup"><span data-stu-id="2a70b-117">If a data source has previously been configured for the project or form, it will appear.</span></span>  
  
3.  <span data-ttu-id="2a70b-118">Tıklatın **proje veri kaynağı Ekle** veri bağlanmak ve bir veri kaynağı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a70b-118">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
4.  <span data-ttu-id="2a70b-119">Üzerinde **veri kaynağı Yapılandırma Sihirbazı** Karşılama sayfasında, tıklatın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="2a70b-119">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="2a70b-120">Üzerinde **bir veri kaynağı türü seç** sayfasında, **veritabanı**.</span><span class="sxs-lookup"><span data-stu-id="2a70b-120">On the **Choose a Data Source Type** page, select **Database**.</span></span>  
  
6.  <span data-ttu-id="2a70b-121">Üzerinde **veri bağlantınızı** sayfasında, kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin.</span><span class="sxs-lookup"><span data-stu-id="2a70b-121">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="2a70b-122">İstenen veri bağlantınızı kullanılabilir seçin değilse **yeni bağlantı** yeni bir veri bağlantısı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="2a70b-122">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>  
  
7.  <span data-ttu-id="2a70b-123">Seçin **Evet, bağlantı kaydetme** uygulama yapılandırma dosyasında bağlantı dizesini kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="2a70b-123">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
8.  <span data-ttu-id="2a70b-124">Uygulamanıza getirmek için veritabanı nesneleri seçin.</span><span class="sxs-lookup"><span data-stu-id="2a70b-124">Select the database objects to bring into your application.</span></span> <span data-ttu-id="2a70b-125">Bu durumda, istediğiniz bir tablodaki bir alan seçin <xref:System.Windows.Forms.TextBox> görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="2a70b-125">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>  
  
9. <span data-ttu-id="2a70b-126">İsterseniz varsayılan veri kümesi adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2a70b-126">Replace the default dataset name if you want.</span></span>  
  
10. <span data-ttu-id="2a70b-127">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2a70b-127">Click **Finish**.</span></span>  
  
11. <span data-ttu-id="2a70b-128">İçinde **özellikleri** penceresinde yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> yeniden özelliği.</span><span class="sxs-lookup"><span data-stu-id="2a70b-128">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="2a70b-129">İçinde **DataSource** UI türü Düzenleyici bağlamak için alanın adını seçin <xref:System.Windows.Forms.TextBox> için.</span><span class="sxs-lookup"><span data-stu-id="2a70b-129">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>  
  
     <span data-ttu-id="2a70b-130">**DataSource** UI türü Düzenleyici kapanır ve veri kümesinin <xref:System.Windows.Forms.BindingSource> ve tablo bağdaştırıcısı belirli veri bağlantısı formunuza eklenir.</span><span class="sxs-lookup"><span data-stu-id="2a70b-130">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a70b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a70b-131">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="2a70b-132">Yeni veri kaynakları ekleyin</span><span class="sxs-lookup"><span data-stu-id="2a70b-132">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)  
 [<span data-ttu-id="2a70b-133">Veri kaynakları penceresi</span><span class="sxs-lookup"><span data-stu-id="2a70b-133">Data Sources Window</span></span>](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
