---
title: Visual Studio'da DPI tanıma devre dışı bırak
description: Windows Form Tasarımcısı'nın HDPI izleyiciler kısıtlamaları ve Visual Studio, DPI kullanmayan bir işlem olarak çalıştırmak nasıl ele alır.
ms.date: 04/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.custom: seoapril2019
ms.openlocfilehash: e52debea382033417afe0bd47f899af1666192bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967238"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a><span data-ttu-id="9cc2d-103">Visual Studio'da DPI tanıma devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="9cc2d-103">Disable DPI-awareness in Visual Studio</span></span>

<span data-ttu-id="9cc2d-104">Visual Studio otomatik olarak görünen ölçekler anlamına gelir inç (DPI) kullanan uygulama başına bir nokta var.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-104">Visual Studio is a dots per inch (DPI) aware application, which means the display scales automatically.</span></span> <span data-ttu-id="9cc2d-105">Uygulamanın DPI kullanan geçersiz olduğunu belirtiyor, işletim sistemi uygulamayı bir bit eşlem olarak ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-105">If an application states that it's not DPI-aware, the operating system scales the application as a bitmap.</span></span> <span data-ttu-id="9cc2d-106">Bu davranış, DPI sanallaştırma olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-106">This behavior is also called DPI virtualization.</span></span> <span data-ttu-id="9cc2d-107">Uygulamayı hala % 100 ölçeklendirme veya 96 DPI çalışır olduğunu düşünüyor.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-107">The application still thinks that it's running at 100% scaling, or 96 dpi.</span></span>

<span data-ttu-id="9cc2d-108">Bu makalede, Windows Form Tasarımcısı'nın HDPI izleyiciler kısıtlamaları ve Visual Studio, DPI kullanmayan bir işlem olarak çalıştırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-108">This article discusses the limitations of Windows Forms Designer on HDPI monitors and how to run Visual Studio as a DPI-unaware process.</span></span>

## <a name="windows-forms-designer-on-hdpi-monitors"></a><span data-ttu-id="9cc2d-109">HDPI monitörde Windows Form Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="9cc2d-109">Windows Forms Designer on HDPI monitors</span></span>

<span data-ttu-id="9cc2d-110">**Windows Form Tasarımcısı** ölçeklendirme desteği, Visual Studio'da yok.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-110">The **Windows Forms Designer** in Visual Studio doesn't have scaling support.</span></span> <span data-ttu-id="9cc2d-111">Bazı formlarında açtığınızda bu görüntü sorunları neden **Windows Form Tasarımcısı** üzerinde yüksek nokta / inç (HDPI) izleyiciler.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-111">This causes display issues when you open some forms in the **Windows Forms Designer** on high dots per inch (HDPI) monitors.</span></span> <span data-ttu-id="9cc2d-112">Örnekler için aşağıdaki görüntüde gösterildiği gibi çakıştırmayı denetimleri görünebilir:</span><span class="sxs-lookup"><span data-stu-id="9cc2d-112">For examples, controls can appear to overlap as shown in the following image:</span></span>

![Windows Form Tasarımcısı HDPI İzleyicisi](./media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

<span data-ttu-id="9cc2d-114">Ndaki bir forma açtığınızda **Windows Form Tasarımcısı** HDPI İzleyicisi Visual Studio'da Visual Studio Tasarımcı üst kısmında sarı bir bilgi çubuğu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="9cc2d-114">When you open a form in the **Windows Forms Designer** in Visual Studio on an HDPI monitor, Visual Studio displays a yellow informational bar at the top of the designer:</span></span>

![DPI uyumlu modda yeniden Visual Studio'da bilgi çubuğu](./media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

<span data-ttu-id="9cc2d-116">İletiyi okur **ölçeklendirme, ana görüntü %200 (192 dpi) ayarlayın. Bu, Tasarımcı penceresinin içinde işleme sorunlara neden olabilir.**</span><span class="sxs-lookup"><span data-stu-id="9cc2d-116">The message reads **Scaling on your main display is set to 200% (192 dpi). This might cause rendering problems in the designer window.**</span></span>

> [!NOTE]
> <span data-ttu-id="9cc2d-117">Bu bilgi çubuğunda Visual Studio 2017 sürüm 15,8 sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-117">This informational bar was introduced in Visual Studio 2017 version 15.8.</span></span>

<span data-ttu-id="9cc2d-118">Tasarımcıda çalışmayan ve formunuzu düzenleme gerekmez bilgi çubuğu yoksay ve Kod Düzenleyicisi'ni veya diğer türde tasarımcıları çalışma devam edin.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-118">If you aren't working in the designer and don't need to adjust the layout of your form, you can ignore the informational bar and continue working in the code editor or in other types of designers.</span></span> <span data-ttu-id="9cc2d-119">(Ayrıca [bildirimleri devre dışı bırak](#disable-notifications) böylece bilgi çubuğu görünmeye devam etmez.) Yalnızca **Windows Form Tasarımcısı** etkilenir.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-119">(You can also [disable notifications](#disable-notifications) so that the informational bar doesn't continue to appear.) Only the **Windows Forms Designer** is affected.</span></span> <span data-ttu-id="9cc2d-120">Çalışmak ihtiyacınız varsa **Windows Form Tasarımcısı**, sonraki bölümde yardımcı [sorununu](#to-resolve-the-display-problem).</span><span class="sxs-lookup"><span data-stu-id="9cc2d-120">If you do need to work in the **Windows Forms Designer**, the next section helps you [resolve the problem](#to-resolve-the-display-problem).</span></span>

## <a name="to-resolve-the-display-problem"></a><span data-ttu-id="9cc2d-121">Görüntüleme sorunu gidermek için</span><span class="sxs-lookup"><span data-stu-id="9cc2d-121">To resolve the display problem</span></span>

<span data-ttu-id="9cc2d-122">Görünen bu sorunu gidermek için kullanabileceğiniz üç seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="9cc2d-122">There are three options to resolve the display problem:</span></span>

1. [<span data-ttu-id="9cc2d-123">DPI kullanmayan bir işlem olarak Visual Studio'yu yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="9cc2d-123">Restart Visual Studio as a DPI-unaware process</span></span>](#restart-visual-studio-as-a-dpi-unaware-process)
2. [<span data-ttu-id="9cc2d-124">Bir kayıt defteri girdisini ekleyin</span><span class="sxs-lookup"><span data-stu-id="9cc2d-124">Add a registry entry</span></span>](#add-a-registry-entry)
3. [<span data-ttu-id="9cc2d-125">Ekranınıza ayarı % 100 ölçeklendirme ayarlayın</span><span class="sxs-lookup"><span data-stu-id="9cc2d-125">Set your display scaling setting to 100%</span></span>](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a><span data-ttu-id="9cc2d-126">DPI kullanmayan bir işlem olarak Visual Studio'yu yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="9cc2d-126">Restart Visual Studio as a DPI-unaware process</span></span>

<span data-ttu-id="9cc2d-127">Sarı bilgi çubuğunda seçeneğini belirleyerek, DPI kullanmayan bir işlem olarak Visual Studio yeniden başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-127">You can restart Visual Studio as a DPI-unaware process by selecting the option on the yellow informational bar.</span></span> <span data-ttu-id="9cc2d-128">Bu sorunu çözümleme tercih edilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-128">This is the preferred way of resolving the problem.</span></span>

<span data-ttu-id="9cc2d-129">Visual Studio, DPI kullanmayan bir işlem olarak çalıştığında, Tasarımcı düzen sorunları çözümlendi ancak yazı tipleri bulanık görünebilir.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-129">When Visual Studio runs as a DPI-unaware process, the designer layout issues are resolved, but fonts may appear blurry.</span></span> <span data-ttu-id="9cc2d-130">Visual Studio bildiren DPI kullanmayan bir işlem olarak çalışır, farklı bir sarı bilgilendirme iletisi görüntüler **Visual Studio, DPI kullanmayan bir işlem olarak çalışıyor. WPF ve XAML tasarımcıları düzgün görüntülenmeyebilir.**</span><span class="sxs-lookup"><span data-stu-id="9cc2d-130">Visual Studio displays a different yellow informational message when it runs as a DPI-unaware process that says **Visual Studio is running as a DPI-unaware process. WPF and XAML designers might not display correctly.**</span></span> <span data-ttu-id="9cc2d-131">Bilgi çubuğu için bir seçenek de sağlar. **DPI kullanan bir işlem olarak Visual Studio'yu yeniden başlatın**.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-131">The informational bar also provides an option to **Restart Visual Studio as a DPI-aware process**.</span></span>

> [!NOTE]
> - <span data-ttu-id="9cc2d-132">Bu araç pencereleri konumunu, DPI kullanmayan bir işlem olarak yeniden başlatma seçeneğini seçtiğinizde Visual Studio araç pencerelerinde akıyor, değişebilir.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-132">If you had undocked tool windows in Visual Studio when you selected the option to restart as a DPI-unaware process, the position of those tool windows may change.</span></span>
> - <span data-ttu-id="9cc2d-133">Varsayılan Visual Basic profil kullanıyorsanız veya varsa **oluşturulduğunda yeni projeleri Kaydet** seçeneği seçili olarak **Araçları** > **seçenekleri**  >  **Projeler ve çözümler**, DPI kullanmayan bir işlem olarak yeniden başlatıldığında, Visual Studio projenizi yeniden açamıyor.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-133">If you use the default Visual Basic profile, or if you have the **Save new projects when created** option deselected in **Tools** > **Options** > **Projects and Solutions**, Visual Studio cannot reopen your project when it restarts as a DPI-unaware process.</span></span> <span data-ttu-id="9cc2d-134">Ancak, proje altında seçerek açabileceğiniz **dosya** > **son projeler ve çözümler**.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-134">However, you can open the project by selecting it under **File** > **Recent Projects and Solutions**.</span></span>

<span data-ttu-id="9cc2d-135">İşiniz bittiğinde çalışan DPI kullanan bir işlem olarak Visual Studio'yu yeniden önemlidir **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-135">It's important to restart Visual Studio as a DPI-aware process when you're finished working in the **Windows Forms Designer**.</span></span> <span data-ttu-id="9cc2d-136">DPI kullanmayan bir işlem olarak çalıştırılırken, yazı tipleri konum bulanık ve diğer tasarımcılar sorunları gibi görebilirsiniz **XAML Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-136">When it's running as a DPI-unaware process, fonts can look blurry and you may see issues in other designers such as the **XAML Designer**.</span></span> <span data-ttu-id="9cc2d-137">Kapatıp DPI uyumlu modda çalışırken Visual Studio, bu duruma DPI kullanan yeniden.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-137">If you close and reopen Visual Studio when it's running in DPI-unaware mode, it becomes DPI-aware again.</span></span> <span data-ttu-id="9cc2d-138">Ayrıca **DPI kullanan bir işlem olarak Visual Studio'yu yeniden başlatın** bilgi çubuğunda seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-138">You can also click the **Restart Visual Studio as a DPI-aware process** option in the informational bar.</span></span>

### <a name="add-a-registry-entry"></a><span data-ttu-id="9cc2d-139">Bir kayıt defteri girdisini ekleyin</span><span class="sxs-lookup"><span data-stu-id="9cc2d-139">Add a registry entry</span></span>

<span data-ttu-id="9cc2d-140">Kayıt defteri değişikliği yaparak Visual Studio DPI uyumlu işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-140">You can mark Visual Studio as DPI-unaware by modifying the registry.</span></span> <span data-ttu-id="9cc2d-141">Açık **Kayıt Defteri Düzenleyicisi'ni** ve bir girdiyi **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** alt anahtarı:</span><span class="sxs-lookup"><span data-stu-id="9cc2d-141">Open **Registry Editor** and add an entry to the **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** subkey:</span></span>

<span data-ttu-id="9cc2d-142">**Giriş**: İster Visual Studio 2017 veya 2019 kullanmakta olduğunuz bağlı olarak, bu değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="9cc2d-142">**Entry**: Depending on whether you're using Visual Studio 2017 or 2019, use one of these values:</span></span>

- <span data-ttu-id="9cc2d-143">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="9cc2d-143">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span></span>
- <span data-ttu-id="9cc2d-144">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="9cc2d-144">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span></span>

> [!NOTE]
> <span data-ttu-id="9cc2d-145">Visual Studio Professional veya Enterprise edition kullanıyorsanız değiştirin **topluluk** ile **Professional** veya **Kurumsal** giriş.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-145">If you're using the Professional or Enterprise edition of Visual Studio, replace **Community** with **Professional** or **Enterprise** in the entry.</span></span> <span data-ttu-id="9cc2d-146">Ayrıca, sürücü harfini gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-146">Also replace the drive letter as necessary.</span></span>

<span data-ttu-id="9cc2d-147">**Tür**: REG_SZ</span><span class="sxs-lookup"><span data-stu-id="9cc2d-147">**Type**: REG_SZ</span></span>

<span data-ttu-id="9cc2d-148">**Değer**: DPIUNAWARE</span><span class="sxs-lookup"><span data-stu-id="9cc2d-148">**Value**: DPIUNAWARE</span></span>

> [!NOTE]
> <span data-ttu-id="9cc2d-149">Kayıt defteri girişini kaldırın kadar visual Studio, DPI kullanmayan modda kalır.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-149">Visual Studio remains in DPI-unaware mode until you remove the registry entry.</span></span>

### <a name="set-your-display-scaling-setting-to-100"></a><span data-ttu-id="9cc2d-150">Ekranınıza ayarı % 100 ölçeklendirme ayarlayın</span><span class="sxs-lookup"><span data-stu-id="9cc2d-150">Set your display scaling setting to 100%</span></span>

<span data-ttu-id="9cc2d-151">Windows 10'da ayarı % 100 ölçeklendirme ekranınıza ayarlamak için şunu yazın **görüntü ayarlarını** görev çubuğunda arama kutusuna tıklayın ve ardından **görünüm ayarlarını değiştirme**.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-151">To set your display scaling setting to 100% in Windows 10, type **display settings** in the task bar search box, and then select **Change display settings**.</span></span> <span data-ttu-id="9cc2d-152">İçinde **ayarları** penceresinde **metin, uygulamaları ve diğer öğelerin boyutunu değiştirme** için **% 100**.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-152">In the **Settings** window, set **Change the size of text, apps, and other items** to **100%**.</span></span>

<span data-ttu-id="9cc2d-153">Kullanıcı arabiriminin kullanılabilmesi için çok küçük zorlaştırabilir çünkü ayarı % 100'e ölçeklendirmeyi ekranınıza istenmeyen, olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-153">Setting your display scaling to 100% may be undesirable, because it can make the user interface too small to be usable.</span></span>

## <a name="disable-notifications"></a><span data-ttu-id="9cc2d-154">Bildirimleri devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="9cc2d-154">Disable notifications</span></span>

<span data-ttu-id="9cc2d-155">DPI değeri bildirilmesini değil, Visual Studio'da sorunları ölçeklendirme seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-155">You can choose not to be notified of DPI scaling issues in Visual Studio.</span></span> <span data-ttu-id="9cc2d-156">Bildirim Tasarımcısı'nda, örneğin çalışmayan durumunda devre dışı bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-156">You might want to disable notifications if you aren't working in the designer, for example.</span></span>

<span data-ttu-id="9cc2d-157">Bildirimleri devre dışı bırakmayı tercih **Araçları** > **seçenekleri** açmak için **seçenekleri** iletişim.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-157">To disable notifications, choose **Tools** > **Options** to open the **Options** dialog.</span></span> <span data-ttu-id="9cc2d-158">Ardından, **Windows Form Tasarımcısı** > **genel**, ayarlayıp **DPI ölçeklendirme bildirimleri** için **False**.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-158">Then, choose **Windows Forms Designer** > **General**, and set **DPI Scaling Notifications** to **False**.</span></span>

![Visual Studio'da bildirimleri seçeneği ölçeklendirme, DPI](./media/disable-dpi-awareness-visual-studio/notifications-option.png)

<span data-ttu-id="9cc2d-160">Ölçeklendirme bildirimleri daha sonra yeniden etkinleştirmek istiyorsanız, özellik kümesine **True**.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-160">If you want to later reenable scaling notifications, set the property to **True**.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="9cc2d-161">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="9cc2d-161">Troubleshoot</span></span>

<span data-ttu-id="9cc2d-162">DPI tanıma geçiş Visual Studio'da beklendiği gibi çalışmıyorsa, sahip olup olmadığını denetleyin `dpiAwareness` değerini **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows nt\currentversion\ımage dosya yürütme Options\devenv.exe**  Kayıt Defteri Düzenleyicisi'nde alt anahtar.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-162">If the DPI-awareness transition isn't working as expected in Visual Studio, check to see if you have the `dpiAwareness` value in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** subkey in Registry Editor.</span></span> <span data-ttu-id="9cc2d-163">Varsa, bu değeri silin.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-163">Delete the value if it's present.</span></span>

## <a name="see-also"></a><span data-ttu-id="9cc2d-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cc2d-164">See also</span></span>

- [<span data-ttu-id="9cc2d-165">Windows Forms'ta otomatik ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="9cc2d-165">Automatic scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
