---
title: Yerelleştirilmiş IntelliSense dosyalarını yükler
description: Geliştirme makinenizi, Visual Studio 'da .NET Core projeleri için yerelleştirilmiş IntelliSense dosyalarını kullanacak şekilde ayarlamayı öğrenin.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157719"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="5fc85-103">.NET Core için yerelleştirilmiş IntelliSense dosyalarını nasıl yükleyeceğiniz</span><span class="sxs-lookup"><span data-stu-id="5fc85-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="5fc85-104">[IntelliSense](/visualstudio/ide/using-intellisense) , Visual Studio gibi farklı tümleşik geliştirme ortamlarında (ides) kullanılabilen bir kod tamamlama yardımıdır.</span><span class="sxs-lookup"><span data-stu-id="5fc85-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="5fc85-105">Varsayılan olarak, .NET Core projelerini geliştirirken, SDK yalnızca IntelliSense dosyalarının Ingilizce sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="5fc85-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="5fc85-106">Bu makalede şunları açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="5fc85-106">This article explains:</span></span>

- <span data-ttu-id="5fc85-107">Bu dosyaların yerelleştirilmiş sürümünü nasıl yükleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc85-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="5fc85-108">Visual Studio yüklemesini farklı bir dil kullanacak şekilde değiştirme.</span><span class="sxs-lookup"><span data-stu-id="5fc85-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5fc85-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5fc85-109">Prerequisites</span></span>

- <span data-ttu-id="5fc85-110">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="5fc85-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="5fc85-111">[Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="5fc85-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="5fc85-112">Yerelleştirilmiş IntelliSense dosyalarını indirme ve yükleme</span><span class="sxs-lookup"><span data-stu-id="5fc85-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fc85-113">Bu yordam, IntelliSense dosyalarını .NET Core yükleme klasörüne kopyalamak için yönetici iznine sahip olmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5fc85-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="5fc85-114">[IntelliSense dosyalarını indirme](https://dotnet.microsoft.com/download/dotnet-core/intellisense) sayfasına gidin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="5fc85-115">Kullanmak istediğiniz dil ve sürüm için IntelliSense dosyasını indirin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="5fc85-116">ZIP dosyasının içeriğini ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="5fc85-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="5fc85-117">.NET Core IntelliSense klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="5fc85-118">.NET Core yükleme klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="5fc85-119">Varsayılan olarak, *%ProgramFiles%\dotnet\packs*altındadır.</span><span class="sxs-lookup"><span data-stu-id="5fc85-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="5fc85-120">IntelliSense 'i yüklemek istediğiniz SDK 'yı seçin ve ilişkili yola gidin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="5fc85-121">Aşağıdaki seçenekleriniz vardır:</span><span class="sxs-lookup"><span data-stu-id="5fc85-121">You have the following options:</span></span>

      | <span data-ttu-id="5fc85-122">SDK türü</span><span class="sxs-lookup"><span data-stu-id="5fc85-122">SDK type</span></span>        | <span data-ttu-id="5fc85-123">Yol</span><span class="sxs-lookup"><span data-stu-id="5fc85-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="5fc85-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5fc85-124">.NET Core</span></span>       | <span data-ttu-id="5fc85-125">*Microsoft. NETCore. app. ref*</span><span class="sxs-lookup"><span data-stu-id="5fc85-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="5fc85-126">Windows Masaüstü</span><span class="sxs-lookup"><span data-stu-id="5fc85-126">Windows Desktop</span></span> | <span data-ttu-id="5fc85-127">*Microsoft. WindowsDesktop. app. ref*</span><span class="sxs-lookup"><span data-stu-id="5fc85-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="5fc85-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="5fc85-128">.NET Standard</span></span>   | <span data-ttu-id="5fc85-129">*NETStandard. Library. ref*</span><span class="sxs-lookup"><span data-stu-id="5fc85-129">*NETStandard.Library.Ref*</span></span>          |

   1. <span data-ttu-id="5fc85-130">Yerelleştirilmiş IntelliSense 'i yüklemek istediğiniz sürüme gidin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="5fc85-131">Örneğin, *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="5fc85-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="5fc85-132">*Ref* klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="5fc85-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="5fc85-133">Bilinen ad klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="5fc85-133">Open the moniker folder.</span></span> <span data-ttu-id="5fc85-134">Örneğin, *netcoreapp 3.1*.</span><span class="sxs-lookup"><span data-stu-id="5fc85-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="5fc85-135">Bu nedenle, gittiğiniz yolun tam yolu *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*şuna benzer.</span><span class="sxs-lookup"><span data-stu-id="5fc85-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="5fc85-136">Yeni açtığınız bilinen ad klasörünün içinde bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5fc85-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="5fc85-137">Klasörün adı, hangi dili kullanmak istediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fc85-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="5fc85-138">Aşağıdaki tabloda farklı seçenekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5fc85-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="5fc85-139">Dil</span><span class="sxs-lookup"><span data-stu-id="5fc85-139">Language</span></span>              | <span data-ttu-id="5fc85-140">Klasör adı</span><span class="sxs-lookup"><span data-stu-id="5fc85-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="5fc85-141">Brezilya Portekizcesi</span><span class="sxs-lookup"><span data-stu-id="5fc85-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="5fc85-142">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="5fc85-142">*pt-br*</span></span>     |
   | <span data-ttu-id="5fc85-143">Çince (Basitleştirilmiş)</span><span class="sxs-lookup"><span data-stu-id="5fc85-143">Chinese (simplified)</span></span>  | <span data-ttu-id="5fc85-144">*zh-Hans*</span><span class="sxs-lookup"><span data-stu-id="5fc85-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="5fc85-145">Çince (Geleneksel)</span><span class="sxs-lookup"><span data-stu-id="5fc85-145">Chinese (traditional)</span></span> | <span data-ttu-id="5fc85-146">*zh-Hant*</span><span class="sxs-lookup"><span data-stu-id="5fc85-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="5fc85-147">Fransızca</span><span class="sxs-lookup"><span data-stu-id="5fc85-147">French</span></span>                | <span data-ttu-id="5fc85-148">*kesir*</span><span class="sxs-lookup"><span data-stu-id="5fc85-148">*fr*</span></span>        |
   | <span data-ttu-id="5fc85-149">Almanca</span><span class="sxs-lookup"><span data-stu-id="5fc85-149">German</span></span>                | <span data-ttu-id="5fc85-150">*seçimini*</span><span class="sxs-lookup"><span data-stu-id="5fc85-150">*de*</span></span>        |
   | <span data-ttu-id="5fc85-151">İtalyanca</span><span class="sxs-lookup"><span data-stu-id="5fc85-151">Italian</span></span>               | <span data-ttu-id="5fc85-152">*içerdiği*</span><span class="sxs-lookup"><span data-stu-id="5fc85-152">*it*</span></span>        |
   | <span data-ttu-id="5fc85-153">Japonca</span><span class="sxs-lookup"><span data-stu-id="5fc85-153">Japanese</span></span>              | <span data-ttu-id="5fc85-154">*Sofya*</span><span class="sxs-lookup"><span data-stu-id="5fc85-154">*ja*</span></span>        |
   | <span data-ttu-id="5fc85-155">Korece</span><span class="sxs-lookup"><span data-stu-id="5fc85-155">Korean</span></span>                | <span data-ttu-id="5fc85-156">*dili*</span><span class="sxs-lookup"><span data-stu-id="5fc85-156">*ko*</span></span>        |
   | <span data-ttu-id="5fc85-157">Rusça</span><span class="sxs-lookup"><span data-stu-id="5fc85-157">Russian</span></span>               | <span data-ttu-id="5fc85-158">*ru*</span><span class="sxs-lookup"><span data-stu-id="5fc85-158">*ru*</span></span>        |
   | <span data-ttu-id="5fc85-159">İspanyolca</span><span class="sxs-lookup"><span data-stu-id="5fc85-159">Spanish</span></span>               | <span data-ttu-id="5fc85-160">*es*</span><span class="sxs-lookup"><span data-stu-id="5fc85-160">*es*</span></span>        |

1. <span data-ttu-id="5fc85-161">Adım 3 ' te ayıkladığınız *. xml* dosyalarını bu yeni klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5fc85-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="5fc85-162">*. Xml* dosyaları SDK klasörleri tarafından bölünür, bu nedenle bunları 4. adımda SEÇTIĞINIZ eşleşen SDK 'ya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5fc85-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="5fc85-163">Visual Studio dilini değiştir</span><span class="sxs-lookup"><span data-stu-id="5fc85-163">Modify Visual Studio language</span></span>

<span data-ttu-id="5fc85-164">Visual Studio 'nun IntelliSense için farklı bir dil kullanabilmesi için, uygun dil paketini de yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc85-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="5fc85-165">Bu, [yükleme sırasında](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) veya daha sonra Visual Studio yüklemesi değiştirilerek yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc85-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="5fc85-166">Seçtiğiniz dilde Visual Studio zaten yapılandırılmışsa, IntelliSense yüklemeniz hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="5fc85-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="5fc85-167">Dil paketini yükler</span><span class="sxs-lookup"><span data-stu-id="5fc85-167">Install the language pack</span></span>

<span data-ttu-id="5fc85-168">İstenen dil paketini kurulum sırasında yüklemediyseniz, dil paketini yüklemek için Visual Studio 'Yu aşağıdaki şekilde güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="5fc85-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fc85-169">Visual Studio 'Yu yüklemek, güncelleştirmek veya değiştirmek için yönetici iznine sahip bir hesapla oturum açmalısınız.</span><span class="sxs-lookup"><span data-stu-id="5fc85-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="5fc85-170">Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5fc85-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="5fc85-171">Bilgisayarınızda Visual Studio yükleyicisi bulun.</span><span class="sxs-lookup"><span data-stu-id="5fc85-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="5fc85-172">Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat**' ı seçin ve ardından **Visual Studio yükleyicisi**olarak listelendiği **V**harfine gidin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Visual Studio Yükleyicisi Windows 'tan açın](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="5fc85-174">Aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5fc85-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="5fc85-175">Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5fc85-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="5fc85-176">Bu durumda, istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="5fc85-177">Yükleyicide, dil paketini eklemek istediğiniz Visual Studio sürümünü bulun ve ardından **Değiştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Visual Studio 'Yu güncelleştirme veya değiştirme](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="5fc85-179">Bir **değiştirme** düğmesi görmüyorsanız ancak bunun yerine bir **güncelleştirme** görüyorsanız, yüklemenizi değiştirebilmeniz için Visual Studio 'yu güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fc85-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="5fc85-180">Güncelleştirme tamamlandıktan sonra **Değiştir** düğmesi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fc85-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="5fc85-181">**Dil paketleri** sekmesinde, yüklemek veya kaldırmak istediğiniz dilleri seçin veya seçimini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5fc85-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Visual Studio dil paketleri sekmesi](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="5fc85-183">**Değiştir**'i seçin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-183">Choose **Modify**.</span></span> <span data-ttu-id="5fc85-184">Güncelleştirme başlar.</span><span class="sxs-lookup"><span data-stu-id="5fc85-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="5fc85-185">Visual Studio 'da dil ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="5fc85-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="5fc85-186">İstenen dil paketlerini yükledikten sonra, Visual Studio ayarlarınızı farklı bir dil kullanacak şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5fc85-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="5fc85-187">Visual Studio’yu açın.</span><span class="sxs-lookup"><span data-stu-id="5fc85-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="5fc85-188">Başlangıç penceresinde, **kod olmadan devam et**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="5fc85-189">Menü çubuğunda **araçlar** > **Seçenekler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="5fc85-190">Seçenekler iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="5fc85-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="5fc85-191">**Ortam** düğümü altında **Uluslararası ayarlar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="5fc85-192">**Dil** açılan çubuğunda istediğiniz dili seçin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="5fc85-193">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-193">Choose **OK**.</span></span>

1. <span data-ttu-id="5fc85-194">Değişikliklerin etkili olması için Visual Studio 'Yu yeniden başlatmanız gerektiğini bildiren bir iletişim kutusu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="5fc85-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="5fc85-195">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="5fc85-195">Choose **OK**.</span></span>

1. <span data-ttu-id="5fc85-196">Visual Studio'yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="5fc85-196">Restart Visual Studio.</span></span>

<span data-ttu-id="5fc85-197">Bundan sonra, yeni yüklediğiniz IntelliSense dosyalarının sürümünü hedefleyen bir .NET Core projesi açtığınızda IntelliSense, beklendiği gibi çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fc85-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fc85-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fc85-198">See also</span></span>

- [<span data-ttu-id="5fc85-199">Visual Studio 'da IntelliSense</span><span class="sxs-lookup"><span data-stu-id="5fc85-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
