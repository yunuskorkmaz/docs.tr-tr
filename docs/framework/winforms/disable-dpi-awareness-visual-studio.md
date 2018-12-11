---
title: Visual Studio'da DPI tanıma devre dışı bırak
description: Windows Form Tasarımcısı HDPI monitörlerde Visual Studio, DPI kullanmayan bir işlem olarak çalıştırmayı öğrenin ve sınırlamalar açıklanır.
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 2d3466476c33a3e5faa8be96d63f1d11442c5d70
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151271"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a><span data-ttu-id="143bf-103">Visual Studio'da DPI tanıma devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="143bf-103">Disable DPI-awareness in Visual Studio</span></span>

<span data-ttu-id="143bf-104">Visual Studio otomatik olarak görünen ölçekler anlamına gelir inç (DPI) kullanan uygulama başına bir nokta var.</span><span class="sxs-lookup"><span data-stu-id="143bf-104">Visual Studio is a dots per inch (DPI) aware application, which means the display scales automatically.</span></span> <span data-ttu-id="143bf-105">Uygulamanın DPI kullanan geçersiz olduğunu belirtiyor, işletim sistemi uygulamayı bir bit eşlem olarak ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="143bf-105">If an application states that it's not DPI-aware, the operating system scales the application as a bitmap.</span></span> <span data-ttu-id="143bf-106">Bu davranış, DPI sanallaştırma olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="143bf-106">This behavior is also called DPI virtualization.</span></span> <span data-ttu-id="143bf-107">Uygulamayı hala % 100 ölçeklendirme veya 96 DPI çalışır olduğunu düşünüyor.</span><span class="sxs-lookup"><span data-stu-id="143bf-107">The application still thinks that it's running at 100% scaling, or 96 dpi.</span></span>

## <a name="windows-forms-designer-on-hdpi-monitors"></a><span data-ttu-id="143bf-108">HDPI monitörde Windows Form Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="143bf-108">Windows Forms Designer on HDPI monitors</span></span>

<span data-ttu-id="143bf-109">**Windows Form Tasarımcısı** ölçeklendirme desteği, Visual Studio'da yok.</span><span class="sxs-lookup"><span data-stu-id="143bf-109">The **Windows Forms Designer** in Visual Studio doesn't have scaling support.</span></span> <span data-ttu-id="143bf-110">Bazı formlarında açtığınızda bu görüntü sorunları neden **Windows Form Tasarımcısı** üzerinde yüksek nokta / inç (HDPI) izleyiciler.</span><span class="sxs-lookup"><span data-stu-id="143bf-110">This causes display issues when you open some forms in the **Windows Forms Designer** on high dots per inch (HDPI) monitors.</span></span> <span data-ttu-id="143bf-111">Örnekler için aşağıdaki görüntüde gösterildiği gibi çakıştırmayı denetimleri görünebilir:</span><span class="sxs-lookup"><span data-stu-id="143bf-111">For examples, controls can appear to overlap as shown in the following image:</span></span>

![Windows Form Tasarımcısı HDPI İzleyicisi](media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

<span data-ttu-id="143bf-113">Visual Studio 2017 sürüm 15,8 ve daha sonra bir formda açtığınızda **Windows Form Tasarımcısı** HDPI izleyicide bir Visual Studio Tasarımcı üst kısmında sarı bir bilgi çubuğu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="143bf-113">In Visual Studio 2017 version 15.8 and later, when you open a form in the **Windows Forms Designer** on an HDPI monitor, Visual Studio displays a yellow informational bar at the top of the designer:</span></span>

![DPI uyumlu modda yeniden Visual Studio'da bilgi çubuğu](media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

<span data-ttu-id="143bf-115">İletiyi okur **ölçeklendirme, ana görüntü %200 (192 dpi) ayarlayın. Bu, Tasarımcı penceresinin içinde işleme sorunlara neden olabilir.**</span><span class="sxs-lookup"><span data-stu-id="143bf-115">The message reads **Scaling on your main display is set to 200% (192 dpi). This might cause rendering problems in the designer window.**</span></span>

<span data-ttu-id="143bf-116">Tasarımcıda çalışmayan ve formunuzu düzenleme gerekmez bilgi çubuğu yoksay ve Kod Düzenleyicisi'ni veya diğer türde tasarımcıları çalışma devam edin.</span><span class="sxs-lookup"><span data-stu-id="143bf-116">If you aren't working in the designer and don't need to adjust the layout of your form, you can ignore the informational bar and continue working in the code editor or in other types of designers.</span></span> <span data-ttu-id="143bf-117">Yalnızca **Windows Form Tasarımcısı** etkilenir.</span><span class="sxs-lookup"><span data-stu-id="143bf-117">Only the **Windows Forms Designer** is affected.</span></span> <span data-ttu-id="143bf-118">Çalışmak ihtiyacınız varsa **Windows Form Tasarımcısı**, sonraki bölümde yardımcı [sorununu](#to-resolve-the-problem).</span><span class="sxs-lookup"><span data-stu-id="143bf-118">If you do need to work in the **Windows Forms Designer**, the next section helps you [resolve the problem](#to-resolve-the-problem).</span></span>

## <a name="to-resolve-the-problem"></a><span data-ttu-id="143bf-119">Bu sorunu gidermek için</span><span class="sxs-lookup"><span data-stu-id="143bf-119">To resolve the problem</span></span>

<span data-ttu-id="143bf-120">Görünen bu sorunu gidermek için kullanabileceğiniz üç seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="143bf-120">There are three options to resolve the display problem.</span></span>

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a><span data-ttu-id="143bf-121">DPI kullanmayan bir işlem olarak Visual Studio'yu yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="143bf-121">Restart Visual Studio as a DPI-unaware process</span></span>

<span data-ttu-id="143bf-122">Sarı bilgi çubuğunda seçeneğini belirleyerek, DPI kullanmayan bir işlem olarak Visual Studio yeniden başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="143bf-122">You can restart Visual Studio as a DPI-unaware process by selecting the option on the yellow informational bar.</span></span> <span data-ttu-id="143bf-123">Bu sorunu çözümleme tercih edilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="143bf-123">This is the preferred way of resolving the problem.</span></span>

<span data-ttu-id="143bf-124">Visual Studio, DPI kullanmayan bir işlem olarak çalıştığında, Tasarımcı düzen sorunları çözümlendi ancak yazı tipleri bulanık görünebilir.</span><span class="sxs-lookup"><span data-stu-id="143bf-124">When Visual Studio runs as a DPI-unaware process, the designer layout issues are resolved, but fonts may appear blurry.</span></span> <span data-ttu-id="143bf-125">Visual Studio bildiren DPI kullanmayan bir işlem olarak çalışır, farklı bir sarı bilgilendirme iletisi görüntüler **Visual Studio, DPI kullanmayan bir işlem olarak çalışıyor. WPF ve XAML tasarımcıları düzgün görüntülenmeyebilir.**</span><span class="sxs-lookup"><span data-stu-id="143bf-125">Visual Studio displays a different yellow informational message when it runs as a DPI-unaware process that says **Visual Studio is running as a DPI-unaware process. WPF and XAML designers might not display correctly.**</span></span> <span data-ttu-id="143bf-126">Bilgi çubuğu için bir seçenek de sağlar. **DPI kullanan bir işlem olarak Visual Studio'yu yeniden başlatın**.</span><span class="sxs-lookup"><span data-stu-id="143bf-126">The informational bar also provides an option to **Restart Visual Studio as a DPI-aware process**.</span></span>

> [!NOTE]
> - <span data-ttu-id="143bf-127">Bu araç pencereleri konumunu, DPI kullanmayan bir işlem olarak yeniden başlatma seçeneğini seçtiğinizde Visual Studio araç pencerelerinde akıyor, değişebilir.</span><span class="sxs-lookup"><span data-stu-id="143bf-127">If you had undocked tool windows in Visual Studio when you selected the option to restart as a DPI-unaware process, the position of those tool windows may change.</span></span>
> - <span data-ttu-id="143bf-128">Varsayılan Visual Basic profil kullanıyorsanız veya varsa **oluşturulduğunda yeni projeleri Kaydet** seçeneği seçili olarak **Araçları** > **seçenekleri**  >  **Projeler ve çözümler**, DPI kullanmayan bir işlem olarak yeniden başlatıldığında, Visual Studio projenizi yeniden açamıyor.</span><span class="sxs-lookup"><span data-stu-id="143bf-128">If you use the default Visual Basic profile, or if you have the **Save new projects when created** option deselected in **Tools** > **Options** > **Projects and Solutions**, Visual Studio cannot reopen your project when it restarts as a DPI-unaware process.</span></span> <span data-ttu-id="143bf-129">Ancak, proje altında seçerek açabileceğiniz **dosya** > **son projeler ve çözümler**.</span><span class="sxs-lookup"><span data-stu-id="143bf-129">However, you can open the project by selecting it under **File** > **Recent Projects and Solutions**.</span></span>

<span data-ttu-id="143bf-130">İşiniz bittiğinde çalışan DPI kullanan bir işlem olarak Visual Studio'yu yeniden önemlidir **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="143bf-130">It's important to restart Visual Studio as a DPI-aware process when you're finished working in the **Windows Forms Designer**.</span></span> <span data-ttu-id="143bf-131">DPI kullanmayan bir işlem olarak çalıştırılırken, yazı tipleri konum bulanık ve diğer tasarımcılar sorunları gibi görebilirsiniz **XAML Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="143bf-131">When it's running as a DPI-unaware process, fonts can look blurry and you may see issues in other designers such as the **XAML Designer**.</span></span> <span data-ttu-id="143bf-132">Kapatıp DPI uyumlu modda çalışırken Visual Studio, bu duruma DPI kullanan yeniden.</span><span class="sxs-lookup"><span data-stu-id="143bf-132">If you close and reopen Visual Studio when it's running in DPI-unaware mode, it becomes DPI-aware again.</span></span> <span data-ttu-id="143bf-133">Ayrıca **DPI kullanan bir işlem olarak Visual Studio'yu yeniden başlatın** bilgi çubuğunda seçeneği.</span><span class="sxs-lookup"><span data-stu-id="143bf-133">You can also click the **Restart Visual Studio as a DPI-aware process** option in the informational bar.</span></span>

### <a name="add-a-registry-entry"></a><span data-ttu-id="143bf-134">Bir kayıt defteri girdisini ekleyin</span><span class="sxs-lookup"><span data-stu-id="143bf-134">Add a registry entry</span></span>

<span data-ttu-id="143bf-135">Kayıt defteri değişikliği yaparak Visual Studio DPI uyumlu işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="143bf-135">You can mark Visual Studio as DPI-unaware by modifying the registry.</span></span> <span data-ttu-id="143bf-136">Açık **Kayıt Defteri Düzenleyicisi'ni** ve bir girdiyi **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** alt anahtarı:</span><span class="sxs-lookup"><span data-stu-id="143bf-136">Open **Registry Editor** and add an entry to the **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** subkey:</span></span>

<span data-ttu-id="143bf-137">**Giriş**: C:\Program dosyaları (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="143bf-137">**Entry**: C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span></span>

   > [!NOTE]
   > <span data-ttu-id="143bf-138">Visual Studio 2017 Professional veya Enterprise edition kullanıyorsanız değiştirin **topluluk** ile **Professional** veya **Kurumsal** giriş.</span><span class="sxs-lookup"><span data-stu-id="143bf-138">If you're using the Professional or Enterprise edition of Visual Studio 2017, replace **Community** with **Professional** or **Enterprise** in the entry.</span></span> <span data-ttu-id="143bf-139">Ayrıca, sürücü harfini gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="143bf-139">Also replace the drive letter as necessary.</span></span>

<span data-ttu-id="143bf-140">**Tür**: REG_SZ</span><span class="sxs-lookup"><span data-stu-id="143bf-140">**Type**: REG_SZ</span></span>

<span data-ttu-id="143bf-141">**Değer**: DPIUNAWARE</span><span class="sxs-lookup"><span data-stu-id="143bf-141">**Value**: DPIUNAWARE</span></span>

> [!NOTE]
> <span data-ttu-id="143bf-142">Kayıt defteri girişini kaldırın kadar visual Studio, DPI kullanmayan modda kalır.</span><span class="sxs-lookup"><span data-stu-id="143bf-142">Visual Studio remains in DPI-unaware mode until you remove the registry entry.</span></span>

### <a name="set-your-display-scaling-setting-to-100"></a><span data-ttu-id="143bf-143">Ekranınıza ayarı % 100 ölçeklendirme ayarlayın</span><span class="sxs-lookup"><span data-stu-id="143bf-143">Set your display scaling setting to 100%</span></span>

<span data-ttu-id="143bf-144">Windows 10'da ayarı % 100 ölçeklendirme ekranınıza ayarlamak için şunu yazın **görüntü ayarlarını** görev çubuğunda arama kutusuna tıklayın ve ardından **görünüm ayarlarını değiştirme**.</span><span class="sxs-lookup"><span data-stu-id="143bf-144">To set your display scaling setting to 100% in Windows 10, type **display settings** in the task bar search box, and then select **Change display settings**.</span></span> <span data-ttu-id="143bf-145">İçinde **ayarları** penceresinde **metin, uygulamaları ve diğer öğelerin boyutunu değiştirme** için **% 100**.</span><span class="sxs-lookup"><span data-stu-id="143bf-145">In the **Settings** window, set **Change the size of text, apps, and other items** to **100%**.</span></span>

<span data-ttu-id="143bf-146">Kullanıcı arabiriminin kullanılabilmesi için çok küçük zorlaştırabilir çünkü ayarı % 100'e ölçeklendirmeyi ekranınıza istenmeyen, olabilir.</span><span class="sxs-lookup"><span data-stu-id="143bf-146">Setting your display scaling to 100% may be undesirable, because it can make the user interface too small to be usable.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="143bf-147">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="143bf-147">Troubleshoot</span></span>

<span data-ttu-id="143bf-148">DPI tanıma geçiş Visual Studio'da beklendiği gibi çalışmıyorsa, sahip olup olmadığını denetleyin `dpiAwareness` değerini **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows nt\currentversion\ımage dosya yürütme Options\devenv.exe**  Kayıt Defteri Düzenleyicisi'nde alt anahtar.</span><span class="sxs-lookup"><span data-stu-id="143bf-148">If the DPI-awareness transition isn't working as expected in Visual Studio, check to see if you have the `dpiAwareness` value in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** subkey in Registry Editor.</span></span> <span data-ttu-id="143bf-149">Varsa, bu değeri silin.</span><span class="sxs-lookup"><span data-stu-id="143bf-149">Delete the value if it's present.</span></span>

## <a name="see-also"></a><span data-ttu-id="143bf-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="143bf-150">See also</span></span>

- [<span data-ttu-id="143bf-151">Windows Forms'ta otomatik ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="143bf-151">Automatic scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
