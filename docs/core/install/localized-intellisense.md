---
title: Yerelleştirilmiş IntelliSense dosyalarını yükler
description: Geliştirme makinenizi, Visual Studio 'da .NET Core projeleri için yerelleştirilmiş IntelliSense dosyalarını kullanacak şekilde ayarlamayı öğrenin.
author: mairaw
ms.author: mairaw
ms.date: 12/18/2019
ms.openlocfilehash: 98d75544ab853e75c175dd2919991b250cfaa3b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443479"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="f2f66-103">.NET Core için yerelleştirilmiş IntelliSense dosyalarını nasıl yükleyeceğiniz</span><span class="sxs-lookup"><span data-stu-id="f2f66-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="f2f66-104">[IntelliSense](/visualstudio/ide/using-intellisense) , Visual Studio gibi farklı tümleşik geliştirme ortamlarında (ides) kullanılabilen bir kod tamamlama yardımıdır.</span><span class="sxs-lookup"><span data-stu-id="f2f66-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="f2f66-105">Varsayılan olarak, .NET Core projelerini geliştirirken, SDK yalnızca IntelliSense dosyalarının Ingilizce sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="f2f66-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="f2f66-106">Bu makalede şunları açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f2f66-106">This article explains:</span></span>

- <span data-ttu-id="f2f66-107">Bu dosyaların yerelleştirilmiş sürümünü nasıl yükleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f2f66-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="f2f66-108">Visual Studio yüklemesini farklı bir dil kullanacak şekilde değiştirme.</span><span class="sxs-lookup"><span data-stu-id="f2f66-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2f66-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f2f66-109">Prerequisites</span></span>

- <span data-ttu-id="f2f66-110">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="f2f66-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="f2f66-111">[Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="f2f66-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="f2f66-112">Yerelleştirilmiş IntelliSense dosyalarını indirme ve yükleme</span><span class="sxs-lookup"><span data-stu-id="f2f66-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2f66-113">Bu yordam, IntelliSense dosyalarını .NET Core yükleme klasörüne kopyalamak için yönetici iznine sahip olmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f2f66-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="f2f66-114">[IntelliSense dosyalarını indirme](https://dotnet.microsoft.com/download/dotnet-core/intellisense) sayfasına gidin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="f2f66-115">Kullanmak istediğiniz dil ve sürüm için IntelliSense dosyasını indirin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="f2f66-116">ZIP dosyasının içeriğini ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="f2f66-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="f2f66-117">.NET Core yükleme klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-117">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="f2f66-118">Varsayılan olarak, *%ProgramFiles%\dotnet\packs*altındadır.</span><span class="sxs-lookup"><span data-stu-id="f2f66-118">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>

   - <span data-ttu-id="f2f66-119">IntelliSense 'i yüklemek istediğiniz SDK 'yı seçin ve ilişkili yola gidin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-119">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="f2f66-120">Şu seçenekleriniz vardır:</span><span class="sxs-lookup"><span data-stu-id="f2f66-120">You have the following options:</span></span>

      | <span data-ttu-id="f2f66-121">SDK türü</span><span class="sxs-lookup"><span data-stu-id="f2f66-121">SDK type</span></span>        | <span data-ttu-id="f2f66-122">Yol</span><span class="sxs-lookup"><span data-stu-id="f2f66-122">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="f2f66-123">.NET Core</span><span class="sxs-lookup"><span data-stu-id="f2f66-123">.NET Core</span></span>       | <span data-ttu-id="f2f66-124">*Microsoft. NETCore. app. ref*</span><span class="sxs-lookup"><span data-stu-id="f2f66-124">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="f2f66-125">Windows Masaüstü</span><span class="sxs-lookup"><span data-stu-id="f2f66-125">Windows Desktop</span></span> | <span data-ttu-id="f2f66-126">*Microsoft. WindowsDesktop. app. ref*</span><span class="sxs-lookup"><span data-stu-id="f2f66-126">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="f2f66-127">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="f2f66-127">.NET Standard</span></span>   | <span data-ttu-id="f2f66-128">*NETStandard. Library. ref*</span><span class="sxs-lookup"><span data-stu-id="f2f66-128">*NETStandard.Library.Ref*</span></span>          |
   
   - <span data-ttu-id="f2f66-129">Yerelleştirilmiş IntelliSense 'i yüklemek istediğiniz sürüme gidin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-129">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="f2f66-130">Örneğin, *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="f2f66-130">For example, *3.1.0*.</span></span>
   - <span data-ttu-id="f2f66-131">*Ref* klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="f2f66-131">Open the *ref* folder.</span></span>
   - <span data-ttu-id="f2f66-132">Bilinen ad klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="f2f66-132">Open the moniker folder.</span></span> <span data-ttu-id="f2f66-133">Örneğin, *netcoreapp 3.1*.</span><span class="sxs-lookup"><span data-stu-id="f2f66-133">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="f2f66-134">Bu nedenle, gittiğiniz yolun tam yolu *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*şuna benzer.</span><span class="sxs-lookup"><span data-stu-id="f2f66-134">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="f2f66-135">Yeni açtığınız bilinen ad klasörünün içinde bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2f66-135">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="f2f66-136">Klasörün adı, hangi dili kullanmak istediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2f66-136">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="f2f66-137">Aşağıdaki tabloda farklı seçenekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f2f66-137">The following table specifies the different options:</span></span>

   | <span data-ttu-id="f2f66-138">Dil</span><span class="sxs-lookup"><span data-stu-id="f2f66-138">Language</span></span>              | <span data-ttu-id="f2f66-139">Klasör adı</span><span class="sxs-lookup"><span data-stu-id="f2f66-139">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="f2f66-140">Brezilya Portekizcesi</span><span class="sxs-lookup"><span data-stu-id="f2f66-140">Brazilian Portuguese</span></span>  | <span data-ttu-id="f2f66-141">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="f2f66-141">*pt-br*</span></span>     |
   | <span data-ttu-id="f2f66-142">Çince (Basitleştirilmiş)</span><span class="sxs-lookup"><span data-stu-id="f2f66-142">Chinese (simplified)</span></span>  | <span data-ttu-id="f2f66-143">*zh-Hans*</span><span class="sxs-lookup"><span data-stu-id="f2f66-143">*zh-hans*</span></span>   |
   | <span data-ttu-id="f2f66-144">Çince (Geleneksel)</span><span class="sxs-lookup"><span data-stu-id="f2f66-144">Chinese (traditional)</span></span> | <span data-ttu-id="f2f66-145">*zh-Hant*</span><span class="sxs-lookup"><span data-stu-id="f2f66-145">*zh-hant*</span></span>   |
   | <span data-ttu-id="f2f66-146">Fransızca</span><span class="sxs-lookup"><span data-stu-id="f2f66-146">French</span></span>                | <span data-ttu-id="f2f66-147">*kesir*</span><span class="sxs-lookup"><span data-stu-id="f2f66-147">*fr*</span></span>        |
   | <span data-ttu-id="f2f66-148">Almanca</span><span class="sxs-lookup"><span data-stu-id="f2f66-148">German</span></span>                | <span data-ttu-id="f2f66-149">*seçimini*</span><span class="sxs-lookup"><span data-stu-id="f2f66-149">*de*</span></span>        |
   | <span data-ttu-id="f2f66-150">İtalyanca</span><span class="sxs-lookup"><span data-stu-id="f2f66-150">Italian</span></span>               | <span data-ttu-id="f2f66-151">*içerdiği*</span><span class="sxs-lookup"><span data-stu-id="f2f66-151">*it*</span></span>        |
   | <span data-ttu-id="f2f66-152">Japonca</span><span class="sxs-lookup"><span data-stu-id="f2f66-152">Japanese</span></span>              | <span data-ttu-id="f2f66-153">*Sofya*</span><span class="sxs-lookup"><span data-stu-id="f2f66-153">*ja*</span></span>        |
   | <span data-ttu-id="f2f66-154">Korece</span><span class="sxs-lookup"><span data-stu-id="f2f66-154">Korean</span></span>                | <span data-ttu-id="f2f66-155">*dili*</span><span class="sxs-lookup"><span data-stu-id="f2f66-155">*ko*</span></span>        |
   | <span data-ttu-id="f2f66-156">Rusça</span><span class="sxs-lookup"><span data-stu-id="f2f66-156">Russian</span></span>               | <span data-ttu-id="f2f66-157">*ru*</span><span class="sxs-lookup"><span data-stu-id="f2f66-157">*ru*</span></span>        |
   | <span data-ttu-id="f2f66-158">İspanyolca</span><span class="sxs-lookup"><span data-stu-id="f2f66-158">Spanish</span></span>               | <span data-ttu-id="f2f66-159">*es*</span><span class="sxs-lookup"><span data-stu-id="f2f66-159">*es*</span></span>        |

1. <span data-ttu-id="f2f66-160">Adım 3 ' te ayıkladığınız *. xml* dosyalarını bu yeni klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f2f66-160">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="f2f66-161">*. Xml* dosyaları SDK klasörleri tarafından bölünür, bu nedenle bunları 4. adımda SEÇTIĞINIZ eşleşen SDK 'ya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f2f66-161">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="f2f66-162">Visual Studio dilini değiştir</span><span class="sxs-lookup"><span data-stu-id="f2f66-162">Modify Visual Studio language</span></span>

<span data-ttu-id="f2f66-163">Visual Studio 'nun IntelliSense için farklı bir dil kullanabilmesi için, uygun dil paketini de yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f2f66-163">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="f2f66-164">Bu, [yükleme sırasında](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) veya daha sonra Visual Studio yüklemesi değiştirilerek yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2f66-164">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="f2f66-165">Seçtiğiniz dilde Visual Studio zaten yapılandırılmışsa, IntelliSense yüklemeniz hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="f2f66-165">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="f2f66-166">Dil paketini yükler</span><span class="sxs-lookup"><span data-stu-id="f2f66-166">Install the language pack</span></span>

<span data-ttu-id="f2f66-167">İstenen dil paketini kurulum sırasında yüklemediyseniz, dil paketini yüklemek için Visual Studio 'Yu aşağıdaki şekilde güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="f2f66-167">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2f66-168">Yüklemek, güncelleştirmek veya Visual Studio değiştirmek için yönetici izinleri olan bir hesapla oturum açmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f2f66-168">To install, update, or modify Visual Studio, you must log on with an account that has administrative permissions.</span></span> <span data-ttu-id="f2f66-169">Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f2f66-169">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="f2f66-170">Bilgisayarınızda Visual Studio yükleyicisi bulun.</span><span class="sxs-lookup"><span data-stu-id="f2f66-170">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="f2f66-171">Örneğin, Windows 10 çalıştıran bir bilgisayarda seçin **Başlat**ve harfi kaydırın **V**, olarak listelenen burada **Visual Studio yükleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="f2f66-171">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Visual Studio Yükleyicisi Windows 'tan açın](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="f2f66-173">Aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f2f66-173">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="f2f66-174">Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f2f66-174">You might have to update the installer before continuing.</span></span> <span data-ttu-id="f2f66-175">Bu durumda, istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-175">If so, follow the prompts.</span></span>

1. <span data-ttu-id="f2f66-176">Yükleyicide, dil paketini eklemek istediğiniz Visual Studio sürümünü bulun ve ardından **Değiştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-176">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Visual Studio 'Yu güncelleştirme veya değiştirme](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="f2f66-178">Bir **değiştirme** düğmesi görmüyorsanız ancak bunun yerine bir **güncelleştirme** görüyorsanız, yüklemenizi değiştirebilmeniz için Visual Studio 'yu güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2f66-178">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="f2f66-179">Güncelleştirme tamamlandıktan sonra **Değiştir** düğmesi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="f2f66-179">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="f2f66-180">**Dil paketleri** sekmesinde, yüklemek veya kaldırmak istediğiniz dilleri seçin veya seçimini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f2f66-180">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Visual Studio dil paketleri sekmesi](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="f2f66-182">**Değiştir**'i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-182">Choose **Modify**.</span></span> <span data-ttu-id="f2f66-183">Güncelleştirme başlar.</span><span class="sxs-lookup"><span data-stu-id="f2f66-183">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="f2f66-184">Visual Studio 'da dil ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="f2f66-184">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="f2f66-185">İstenen dil paketlerini yükledikten sonra, Visual Studio ayarlarınızı farklı bir dil kullanacak şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f2f66-185">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="f2f66-186">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="f2f66-186">Open Visual Studio.</span></span>

1. <span data-ttu-id="f2f66-187">Başlangıç penceresinde, **kod olmadan devam et**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-187">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="f2f66-188">Ana menüde **araçlar** > **Seçenekler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-188">On the main menu, select **Tools** > **Options**.</span></span> <span data-ttu-id="f2f66-189">Seçenekler iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="f2f66-189">The Options dialog opens.</span></span>

1. <span data-ttu-id="f2f66-190">**Ortam** klasörü altında **Uluslararası ayarlar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-190">Under the **Environment** folder, choose **International Settings**.</span></span>

1. <span data-ttu-id="f2f66-191">**Dil** açılan çubuğunda istediğiniz dili seçin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-191">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="f2f66-192">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-192">Choose **OK**.</span></span> 

1. <span data-ttu-id="f2f66-193">Değişikliklerin etkili olması için Visual Studio 'Yu yeniden başlatmanız gerektiğini bildiren bir iletişim kutusu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="f2f66-193">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="f2f66-194">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f2f66-194">Choose **OK**.</span></span>

1. <span data-ttu-id="f2f66-195">Visual Studio'yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="f2f66-195">Restart Visual Studio.</span></span>

<span data-ttu-id="f2f66-196">Bundan sonra, yeni yüklediğiniz IntelliSense dosyalarının sürümünü hedefleyen bir .NET Core projesi açtığınızda IntelliSense, beklendiği gibi çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2f66-196">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2f66-197">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2f66-197">See also</span></span>

- [<span data-ttu-id="f2f66-198">Visual Studio 'da IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f2f66-198">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
