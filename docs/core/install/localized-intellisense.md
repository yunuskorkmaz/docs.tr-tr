---
title: Yerelleştirilmiş IntelliSense dosyalarını yükleme
description: Visual Studio'daki .NET Core projeleri için yerelleştirilmiş IntelliSense dosyalarını kullanmak üzere geliştirme makinenizi nasıl ayarlayabilirsiniz öğrenin.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157719"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="05cde-103">.NET Core için yerelleştirilmiş IntelliSense dosyaları nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="05cde-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="05cde-104">[IntelliSense,](/visualstudio/ide/using-intellisense) Visual Studio gibi farklı tümleşik geliştirme ortamlarında (IME' ler) kullanılabilen bir kod tamamlama yardımıdır.</span><span class="sxs-lookup"><span data-stu-id="05cde-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="05cde-105">Varsayılan olarak, .NET Core projeleri geliştirirken, SDK yalnızca IntelliSense dosyalarının İngilizce sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="05cde-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="05cde-106">Bu makalede açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="05cde-106">This article explains:</span></span>

- <span data-ttu-id="05cde-107">Bu dosyaların yerelleştirilmiş sürümünü yükleme.</span><span class="sxs-lookup"><span data-stu-id="05cde-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="05cde-108">Farklı bir dil kullanmak için Visual Studio yüklemesi nasıl değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="05cde-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="05cde-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="05cde-109">Prerequisites</span></span>

- <span data-ttu-id="05cde-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya daha sonraki bir sürüm.</span><span class="sxs-lookup"><span data-stu-id="05cde-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="05cde-111">[Visual Studio 2019 sürüm 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya daha sonraki bir sürüm.</span><span class="sxs-lookup"><span data-stu-id="05cde-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="05cde-112">Yerelleştirilmiş IntelliSense dosyalarını indirin ve kurun</span><span class="sxs-lookup"><span data-stu-id="05cde-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05cde-113">Bu yordam, IntelliSense dosyalarını .NET Core yükleme klasörüne kopyalamak için yönetici iznine sahip olmayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="05cde-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="05cde-114">[IntelliSense dosyalarını indir](https://dotnet.microsoft.com/download/dotnet-core/intellisense) sayfasına gidin.</span><span class="sxs-lookup"><span data-stu-id="05cde-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="05cde-115">Kullanmak istediğiniz dil ve sürüm için IntelliSense dosyasını indirin.</span><span class="sxs-lookup"><span data-stu-id="05cde-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="05cde-116">Zip dosyasının içeriğini ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="05cde-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="05cde-117">.NET Core Intellisense klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="05cde-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="05cde-118">.NET Core yükleme klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="05cde-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="05cde-119">Varsayılan olarak, *%ProgramFiles%\dotnet\packs*altındadır.</span><span class="sxs-lookup"><span data-stu-id="05cde-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="05cde-120">IntelliSense'i yüklemek istediğiniz SDK'yı seçin ve ilişkili yola gidin.</span><span class="sxs-lookup"><span data-stu-id="05cde-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="05cde-121">Aşağıdaki seçenekleriniz vardır:</span><span class="sxs-lookup"><span data-stu-id="05cde-121">You have the following options:</span></span>

      | <span data-ttu-id="05cde-122">SDK türü</span><span class="sxs-lookup"><span data-stu-id="05cde-122">SDK type</span></span>        | <span data-ttu-id="05cde-123">Yol</span><span class="sxs-lookup"><span data-stu-id="05cde-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="05cde-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="05cde-124">.NET Core</span></span>       | <span data-ttu-id="05cde-125">*Microsoft.NETCore.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="05cde-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="05cde-126">Windows Masaüstü</span><span class="sxs-lookup"><span data-stu-id="05cde-126">Windows Desktop</span></span> | <span data-ttu-id="05cde-127">*Microsoft.WindowsDesktop.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="05cde-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="05cde-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="05cde-128">.NET Standard</span></span>   | <span data-ttu-id="05cde-129">*NETStandard.Library.Ref*</span><span class="sxs-lookup"><span data-stu-id="05cde-129">*NETStandard.Library.Ref*</span></span>          |

   1. <span data-ttu-id="05cde-130">Yerelleştirilmiş IntelliSense'i yüklemek istediğiniz sürüme gidin.</span><span class="sxs-lookup"><span data-stu-id="05cde-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="05cde-131">Örneğin, *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="05cde-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="05cde-132">*Ref* klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="05cde-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="05cde-133">Takma addklasörü açın.</span><span class="sxs-lookup"><span data-stu-id="05cde-133">Open the moniker folder.</span></span> <span data-ttu-id="05cde-134">Örneğin, *netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="05cde-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="05cde-135">Yani, gitmek istiyorum tam yol C benzer *görünecektir:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="05cde-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="05cde-136">Az önce açtığınız takma addklasörün içinde bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05cde-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="05cde-137">Klasörün adı hangi dili kullanmak istediğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="05cde-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="05cde-138">Aşağıdaki tabloda farklı seçenekler belirtin:</span><span class="sxs-lookup"><span data-stu-id="05cde-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="05cde-139">Dil</span><span class="sxs-lookup"><span data-stu-id="05cde-139">Language</span></span>              | <span data-ttu-id="05cde-140">Klasör adı</span><span class="sxs-lookup"><span data-stu-id="05cde-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="05cde-141">Brezilya Portekizcesi</span><span class="sxs-lookup"><span data-stu-id="05cde-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="05cde-142">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="05cde-142">*pt-br*</span></span>     |
   | <span data-ttu-id="05cde-143">Çince (basitleştirilmiş)</span><span class="sxs-lookup"><span data-stu-id="05cde-143">Chinese (simplified)</span></span>  | <span data-ttu-id="05cde-144">*zh-hans*</span><span class="sxs-lookup"><span data-stu-id="05cde-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="05cde-145">Çince (geleneksel)</span><span class="sxs-lookup"><span data-stu-id="05cde-145">Chinese (traditional)</span></span> | <span data-ttu-id="05cde-146">*zh-hant*</span><span class="sxs-lookup"><span data-stu-id="05cde-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="05cde-147">Fransızca</span><span class="sxs-lookup"><span data-stu-id="05cde-147">French</span></span>                | <span data-ttu-id="05cde-148">*Fr*</span><span class="sxs-lookup"><span data-stu-id="05cde-148">*fr*</span></span>        |
   | <span data-ttu-id="05cde-149">Almanca</span><span class="sxs-lookup"><span data-stu-id="05cde-149">German</span></span>                | <span data-ttu-id="05cde-150">*de*</span><span class="sxs-lookup"><span data-stu-id="05cde-150">*de*</span></span>        |
   | <span data-ttu-id="05cde-151">İtalyanca</span><span class="sxs-lookup"><span data-stu-id="05cde-151">Italian</span></span>               | <span data-ttu-id="05cde-152">*bu*</span><span class="sxs-lookup"><span data-stu-id="05cde-152">*it*</span></span>        |
   | <span data-ttu-id="05cde-153">Japonca</span><span class="sxs-lookup"><span data-stu-id="05cde-153">Japanese</span></span>              | <span data-ttu-id="05cde-154">*Ja*</span><span class="sxs-lookup"><span data-stu-id="05cde-154">*ja*</span></span>        |
   | <span data-ttu-id="05cde-155">Korece</span><span class="sxs-lookup"><span data-stu-id="05cde-155">Korean</span></span>                | <span data-ttu-id="05cde-156">*ko*</span><span class="sxs-lookup"><span data-stu-id="05cde-156">*ko*</span></span>        |
   | <span data-ttu-id="05cde-157">Rusça</span><span class="sxs-lookup"><span data-stu-id="05cde-157">Russian</span></span>               | <span data-ttu-id="05cde-158">*Ru*</span><span class="sxs-lookup"><span data-stu-id="05cde-158">*ru*</span></span>        |
   | <span data-ttu-id="05cde-159">İspanyolca</span><span class="sxs-lookup"><span data-stu-id="05cde-159">Spanish</span></span>               | <span data-ttu-id="05cde-160">*Es*</span><span class="sxs-lookup"><span data-stu-id="05cde-160">*es*</span></span>        |

1. <span data-ttu-id="05cde-161">Adım 3'te ayıkladığınız *.xml* dosyalarını bu yeni klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="05cde-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="05cde-162">*.xml* dosyaları SDK klasörlerine göre ayrılmıştır, bu nedenle bunları adım 4'te seçtiğiniz eşleşen SDK'ya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="05cde-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="05cde-163">Visual Studio dilini değiştirin</span><span class="sxs-lookup"><span data-stu-id="05cde-163">Modify Visual Studio language</span></span>

<span data-ttu-id="05cde-164">Visual Studio'nun IntelliSense için farklı bir dil kullanması için uygun dil paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="05cde-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="05cde-165">Bu, [yükleme sırasında](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) veya daha sonra Visual Studio yüklemesini değiştirerek yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="05cde-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="05cde-166">Visual Studio'yu seçtiğiniz dile göre yapılandırmışsanız, IntelliSense yüklemeniz hazırdır.</span><span class="sxs-lookup"><span data-stu-id="05cde-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="05cde-167">Dil paketini yükleme</span><span class="sxs-lookup"><span data-stu-id="05cde-167">Install the language pack</span></span>

<span data-ttu-id="05cde-168">Kurulum sırasında istediğiniz dil paketini yüklemediyseniz, dil paketini yüklemek için Visual Studio'yu aşağıdaki gibi güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="05cde-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05cde-169">Visual Studio'yı yüklemek, güncellemek veya değiştirmek için yönetici izni olan bir hesapla oturum açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05cde-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="05cde-170">Daha fazla bilgi için [Kullanıcı izinlerine ve Visual Studio'ya](/visualstudio/ide/user-permissions-and-visual-studio)bakın.</span><span class="sxs-lookup"><span data-stu-id="05cde-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="05cde-171">Bilgisayarınızda Visual Studio Yükleyicisini bulun.</span><span class="sxs-lookup"><span data-stu-id="05cde-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="05cde-172">Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat'ı**seçin ve ardından Visual **Studio Installer**olarak listelenen **V**harfine gidin.</span><span class="sxs-lookup"><span data-stu-id="05cde-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Windows'tan Visual Studio Yükleyicisini Açın](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="05cde-174">Visual Studio Yükleyicisini aşağıdaki konumda da bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="05cde-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="05cde-175">Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="05cde-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="05cde-176">Öyleyse, istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="05cde-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="05cde-177">Yükleyicide, dil paketini eklemek istediğiniz Visual Studio sürümünü arayın ve ardından **Değiştir'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="05cde-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Visual Studio'yı güncelleştirin veya değiştirin](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="05cde-179">**Değiştir** düğmesi görmüyorsanız ancak bunun yerine bir **Güncelleme** düğmesi görüyorsanız, yüklemenizi değiştirebilmeniz için Visual Studio'nuzu güncellemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05cde-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="05cde-180">Güncelleştirme tamamlandıktan sonra **Değiştir** düğmesi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="05cde-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="05cde-181">Dil **paketleri** sekmesinde, yüklemek veya kaldırmak istediğiniz dilleri seçin veya seçin.</span><span class="sxs-lookup"><span data-stu-id="05cde-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Visual Studio dil paketleri sekmesi](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="05cde-183">**Değiştir'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="05cde-183">Choose **Modify**.</span></span> <span data-ttu-id="05cde-184">Güncelleştirme başlar.</span><span class="sxs-lookup"><span data-stu-id="05cde-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="05cde-185">Visual Studio'da dil ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="05cde-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="05cde-186">İstediğiniz dil paketlerini yükledikten sonra Visual Studio ayarlarınızı farklı bir dil kullanacak şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="05cde-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="05cde-187">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="05cde-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="05cde-188">Başlangıç penceresinde, **kodsuz Devam**et'i seçin.</span><span class="sxs-lookup"><span data-stu-id="05cde-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="05cde-189">Menü çubuğunda **Araçlar** > **Seçenekleri'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="05cde-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="05cde-190">Seçenekler iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="05cde-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="05cde-191">**Çevre** düğümü altında, **Uluslararası Ayarlar'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="05cde-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="05cde-192">**Dil** açılır tarihinde istediğiniz dili seçin.</span><span class="sxs-lookup"><span data-stu-id="05cde-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="05cde-193">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="05cde-193">Choose **OK**.</span></span>

1. <span data-ttu-id="05cde-194">Bir iletişim kutusu, değişikliklerin etkili olması için Visual Studio'yu yeniden başlatmanız gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="05cde-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="05cde-195">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="05cde-195">Choose **OK**.</span></span>

1. <span data-ttu-id="05cde-196">Visual Studio'yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="05cde-196">Restart Visual Studio.</span></span>

<span data-ttu-id="05cde-197">Bundan sonra, IntelliSense'iniz, yeni yüklediğiniz IntelliSense dosyalarının sürümünü hedefleyen bir .NET Core projesini açtığınızda beklendiği gibi çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05cde-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="05cde-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05cde-198">See also</span></span>

- [<span data-ttu-id="05cde-199">IntelliSense in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="05cde-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
