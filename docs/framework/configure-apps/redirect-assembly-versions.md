---
title: Derleme Sürümlerini Yönlendirme
description: Derleme zamanı bağlama başvurularını .NET derlemelerinin, üçüncü taraf derlemelerin veya kendi uygulamanızın derlemelerinizin farklı sürümlerine yeniden yönlendirin.
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
ms.openlocfilehash: f0db5c32ba12b8e5313ca363e82260d66a7c010f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166904"
---
# <a name="redirecting-assembly-versions"></a><span data-ttu-id="c6c61-103">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="c6c61-103">Redirecting Assembly Versions</span></span>

<span data-ttu-id="c6c61-104">Derleme zamanı bağlama başvurularını .NET Framework derlemelere, üçüncü taraf derlemelerine veya kendi uygulamanızın derlemelerinize yeniden yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-104">You can redirect compile-time binding references to .NET Framework assemblies, third-party assemblies, or your own app's assemblies.</span></span> <span data-ttu-id="c6c61-105">Uygulamanızı çeşitli yollarla bir derlemenin farklı bir sürümünü kullanacak şekilde yeniden yönlendirebilirsiniz: Yayımcı ilkesi aracılığıyla uygulama yapılandırma dosyası aracılığıyla; veya makine yapılandırma dosyası aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="c6c61-105">You can redirect your app to use a different version of an assembly in a number of ways: through publisher policy, through an app configuration file; or through the machine configuration file.</span></span> <span data-ttu-id="c6c61-106">Bu makalede, derleme bağlamasının .NET Framework nasıl çalıştığı ve nasıl yapılandırılabileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6c61-106">This article discusses how assembly binding works in the .NET Framework and how it can be configured.</span></span>

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>

## <a name="assembly-unification-and-default-binding"></a><span data-ttu-id="c6c61-107">Derleme birleşme ve varsayılan bağlama</span><span class="sxs-lookup"><span data-stu-id="c6c61-107">Assembly unification and default binding</span></span>

 <span data-ttu-id="c6c61-108">.NET Framework derlemelerine bağlamalar bazen *derleme birleşme*adlı bir işlem aracılığıyla yeniden yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-108">Bindings to .NET Framework assemblies are sometimes redirected through a process called *assembly unification*.</span></span> <span data-ttu-id="c6c61-109">.NET Framework, ortak dil çalışma zamanının bir sürümünden ve tür kitaplığını oluşturan iki düzine .NET Framework bütünleştirilmiş kod ile oluşur.</span><span class="sxs-lookup"><span data-stu-id="c6c61-109">The .NET Framework consists of a version of the common language runtime and about two dozen .NET Framework assemblies that make up the type library.</span></span> <span data-ttu-id="c6c61-110">Bu .NET Framework derlemeleri çalışma zamanı tarafından tek bir birim olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-110">These .NET Framework assemblies are treated by the runtime as a single unit.</span></span> <span data-ttu-id="c6c61-111">Varsayılan olarak, bir uygulama başlatıldığında, çalışma zamanı tarafından çalıştırılan koddaki türlere yapılan tüm başvurular, bir işlemde yüklenen çalışma zamanıyla aynı sürüm numarasına sahip .NET Framework derlemelere yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-111">By default, when an app is launched, all references to types in code run by the runtime are directed to .NET Framework assemblies that have the same version number as the runtime that is loaded in a process.</span></span> <span data-ttu-id="c6c61-112">Bu modelde gerçekleşen yeniden yönlendirmeler, çalışma zamanının varsayılan davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="c6c61-112">The redirections that occur with this model are the default behavior for the runtime.</span></span>

 <span data-ttu-id="c6c61-113">Örneğin, uygulamanız System.XML ad alanındaki türlere başvuruyorsa ve .NET Framework 4,5 kullanılarak oluşturulduysa, çalışma zamanı sürüm 4,5 ile birlikte gelen System.XML derlemesine statik başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-113">For example, if your app references types in the System.XML namespace and was built by using the .NET Framework 4.5, it contains static references to the System.XML assembly that ships with runtime version 4.5.</span></span> <span data-ttu-id="c6c61-114">Bağlama başvurusunu .NET Framework 4 ile birlikte gelen System.XML derlemesine işaret etmek istiyorsanız, yeniden yönlendirme bilgilerini uygulama yapılandırma dosyasına yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-114">If you want to redirect the binding reference to point to the System.XML assembly that ship with the .NET Framework 4, you can put redirect information in the app configuration file.</span></span> <span data-ttu-id="c6c61-115">Birleştirilmiş bir .NET Framework derlemesi için yapılandırma dosyasında bir bağlama yeniden yönlendirmesi, bu derleme için birleşme işlemini iptal eder.</span><span class="sxs-lookup"><span data-stu-id="c6c61-115">A binding redirection in a configuration file for a unified .NET Framework assembly cancels the unification for that assembly.</span></span>

 <span data-ttu-id="c6c61-116">Ayrıca, birden çok sürüm varsa, üçüncü taraf derlemeler için derleme bağlamayı el ile yeniden yönlendirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-116">In addition, you may want to manually redirect assembly binding for third-party assemblies if there are multiple versions available.</span></span>

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>

## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a><span data-ttu-id="c6c61-117">Yayımcı ilkesini kullanarak derleme sürümlerini yeniden yönlendirme</span><span class="sxs-lookup"><span data-stu-id="c6c61-117">Redirecting assembly versions by using publisher policy</span></span>

 <span data-ttu-id="c6c61-118">Derlemelerin satıcıları, yeni derlemeyle bir yayımcı ilke dosyası ekleyerek uygulamaları bir derlemenin daha yeni bir sürümüne yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-118">Vendors of assemblies can direct apps to a newer version of an assembly by including a publisher policy file with the new assembly.</span></span> <span data-ttu-id="c6c61-119">Genel derleme önbelleğinde bulunan Yayımcı ilke dosyası, derleme yeniden yönlendirme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-119">The publisher policy file, which is located in the global assembly cache, contains assembly redirection settings.</span></span>

 <span data-ttu-id="c6c61-120">Her *önemli*. bir derlemenin *İkincil* sürümünün kendi yayımcı ilkesi dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="c6c61-120">Each *major*.*minor* version of an assembly has its own publisher policy file.</span></span> <span data-ttu-id="c6c61-121">Örneğin, sürüm 2,0 ile ilişkili olduklarından, 2.0.2.222 sürümünden 2.0.3.000 'e ve sürüm 2.0.2.321 'den sürüm 2.0.3.000 'e yeniden yönlendirmeler aynı dosyaya gider.</span><span class="sxs-lookup"><span data-stu-id="c6c61-121">For example, redirections from version 2.0.2.222 to 2.0.3.000 and from version 2.0.2.321 to version 2.0.3.000 both go into the same file, because they are associated with version 2.0.</span></span> <span data-ttu-id="c6c61-122">Ancak, sürüm 3.0.0.999 'den sürüm 4.0.0.000 'e yeniden yönlendirme, sürüm 3.0.999 için dosyaya gider.</span><span class="sxs-lookup"><span data-stu-id="c6c61-122">However, a redirection from version 3.0.0.999 to version 4.0.0.000 goes into the file for version 3.0.999.</span></span> <span data-ttu-id="c6c61-123">.NET Framework her ana sürümünün kendi yayımcı ilkesi dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="c6c61-123">Each major version of the .NET Framework has its own publisher policy file.</span></span>

 <span data-ttu-id="c6c61-124">Bir derleme için yayımcı ilke dosyası varsa, çalışma zamanı derlemenin bildirimini ve uygulama yapılandırma dosyasını denetledikten sonra bu dosyayı denetler.</span><span class="sxs-lookup"><span data-stu-id="c6c61-124">If a publisher policy file exists for an assembly, the runtime checks this file after checking the assembly's manifest and app configuration file.</span></span> <span data-ttu-id="c6c61-125">Satıcıların Yayımcı ilke dosyalarını yalnızca yeni derleme yeniden yönlendirilmekte olan derleme ile geriye dönük olarak uyumlu olduğunda kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-125">Vendors should use publisher policy files only when the new assembly is backward compatible with the assembly being redirected.</span></span>

 <span data-ttu-id="c6c61-126">[Yayımcı Ilkesini atlama bölümünde](#bypass_PP)açıklandığı gibi, uygulama yapılandırma dosyasında ayarları belirterek uygulamanız için yayımcı ilkesini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-126">You can bypass publisher policy for your app by specifying settings in the app configuration file, as discussed in the [Bypassing publisher policy section](#bypass_PP).</span></span>

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>

## <a name="redirecting-assembly-versions-at-the-app-level"></a><span data-ttu-id="c6c61-127">Uygulama düzeyinde derleme sürümlerini yeniden yönlendirme</span><span class="sxs-lookup"><span data-stu-id="c6c61-127">Redirecting assembly versions at the app level</span></span>

 <span data-ttu-id="c6c61-128">Uygulama yapılandırma dosyası aracılığıyla uygulamanız için bağlama davranışını değiştirmek için birkaç farklı teknik vardır: dosyayı el ile düzenleyebilirsiniz, otomatik bağlama yeniden yönlendirmesine güvenebilirsiniz veya yayımcı ilkesini atlayarak bağlama davranışını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-128">There are a few different techniques for changing the binding behavior for your app through the app configuration file: you can manually edit the file, you can rely on automatic binding redirection, or you can specify binding behavior by bypassing publisher policy.</span></span>

### <a name="manually-editing-the-app-config-file"></a><span data-ttu-id="c6c61-129">Uygulama yapılandırma dosyasını el ile düzenleyin</span><span class="sxs-lookup"><span data-stu-id="c6c61-129">Manually editing the app config file</span></span>

 <span data-ttu-id="c6c61-130">Derleme sorunlarını gidermek için uygulama yapılandırma dosyasını el ile düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-130">You can manually edit the app configuration file to resolve assembly issues.</span></span> <span data-ttu-id="c6c61-131">Örneğin, bir satıcı bir yayımcı ilkesi sağlamadan uygulamanızın kullandığı daha yeni bir sürümünü serbest bırakabilir, çünkü geriye dönük uyumluluğu garanti etmez, derleme bağlama bilgilerini uygulamanızın yapılandırma dosyasına aşağıdaki gibi yerleştirerek, uygulamanızı derlemenin daha yeni bir sürümünü kullanacak şekilde yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-131">For example, if a vendor might release a newer version of an assembly that your app uses without supplying a publisher policy, because they do not guarantee backward compatibility, you can direct your app to use the newer version of the assembly by putting assembly binding information in your app's configuration file as follows.</span></span>

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a><span data-ttu-id="c6c61-132">Otomatik bağlama yeniden yönlendirmesine bağlı</span><span class="sxs-lookup"><span data-stu-id="c6c61-132">Relying on automatic binding redirection</span></span>

<span data-ttu-id="c6c61-133">Visual Studio 'da .NET Framework 4.5.1 veya sonraki bir sürümü hedefleyen bir masaüstü uygulaması oluşturduğunuzda, uygulama otomatik bağlama yeniden yönlendirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6c61-133">When you create a desktop app in Visual Studio that targets the .NET Framework 4.5.1 or a later version, the app uses automatic binding redirection.</span></span> <span data-ttu-id="c6c61-134">Bu, iki bileşen aynı tanımlayıcı adlı derlemenin farklı sürümlerine başvurmışsa, çalışma zamanının çıkış uygulaması yapılandırma (app.config) dosyasındaki derlemenin daha yeni sürümüne otomatik olarak bir bağlama yeniden yönlendirmesi eklemesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-134">This means that if two components reference different versions of the same strong-named assembly, the runtime automatically adds a binding redirection to the newer version of the assembly in the output app configuration (app.config) file.</span></span> <span data-ttu-id="c6c61-135">Bu yeniden yönlendirme, başka bir şekilde gerçekleşmiş olabilecek derleme birleşme özelliğini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c6c61-135">This redirection overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="c6c61-136">Kaynak app.config dosyası değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="c6c61-136">The source app.config file is not modified.</span></span> <span data-ttu-id="c6c61-137">Örneğin, uygulamanızın bir bant dışı .NET Framework bileşenine doğrudan başvurmasına, ancak aynı bileşenin eski bir sürümünü hedefleyen bir üçüncü taraf kitaplığı kullandığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c6c61-137">For example, let's say that your app directly references an out-of-band .NET Framework component but uses a third-party library that targets an older version of the same component.</span></span> <span data-ttu-id="c6c61-138">Uygulamayı derlerken, çıkış uygulama yapılandırma dosyası, bileşenin daha yeni sürümüne bir bağlama yeniden yönlendirmesi içerecek şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-138">When you compile the app, the output app configuration file is modified to contain a binding redirection to the newer version of the component.</span></span> <span data-ttu-id="c6c61-139">Bir Web uygulaması oluşturursanız, bağlama çakışmasıyla ilgili olarak bir derleme uyarısı alırsınız, bu da kaynak Web yapılandırma dosyasına gerekli bağlama yeniden yönlendirmesini ekleme seçeneği sunar.</span><span class="sxs-lookup"><span data-stu-id="c6c61-139">If you create a web app, you receive a build warning regarding the binding conflict, which in turn, gives you the option to add the necessary binding redirect to the source web configuration file.</span></span>

<span data-ttu-id="c6c61-140">Derleme zamanında kaynak app.config dosyasına el ile bağlama yeniden yönlendirmeleri eklerseniz, Visual Studio, eklediğiniz bağlama yeniden yönlendirmeleri temelinde derlemeleri birleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="c6c61-140">If you manually add binding redirects to the source app.config file, at compile time, Visual Studio tries to unify the assemblies based on the binding redirects you added.</span></span> <span data-ttu-id="c6c61-141">Örneğin, bir derleme için aşağıdaki bağlama yeniden yönlendirmesini eklemenizi söyleyin:</span><span class="sxs-lookup"><span data-stu-id="c6c61-141">For example, let's say you insert the following binding redirect for an assembly:</span></span>

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

<span data-ttu-id="c6c61-142">Uygulamanızdaki başka bir proje aynı derlemenin 1.0.0.0 sürümüne başvuruyorsa, otomatik bağlama yeniden yönlendirme, uygulamanın bu derlemenin sürüm 2.0.0.0 üzerinde birleştirilmiş olması için çıkış app.config dosyasına aşağıdaki girişi ekler:</span><span class="sxs-lookup"><span data-stu-id="c6c61-142">If another project in your app references version 1.0.0.0 of the same assembly, automatic binding redirection adds the following entry to the output app.config file so that the app is unified on version 2.0.0.0 of this assembly:</span></span>

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

<span data-ttu-id="c6c61-143">Uygulamanız .NET Framework eski sürümlerini hedefliyorsa otomatik bağlama yeniden yönlendirmesini etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-143">You can enable automatic binding redirection if your app targets older versions of the .NET Framework.</span></span> <span data-ttu-id="c6c61-144">Herhangi bir derleme için app.config dosyasında bağlama yeniden yönlendirme bilgilerini sağlayarak veya bağlama yeniden yönlendirme özelliğini kapatarak bu varsayılan davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-144">You can override this default behavior by providing binding redirection information in the app.config file for any assembly, or by turning off the binding redirection feature.</span></span> <span data-ttu-id="c6c61-145">Bu özelliğin nasıl etkinleştirileceği veya devre dışı bırakılacağı hakkında bilgi için bkz. [nasıl yapılır: etkinleştirme ve devre dışı bırakma otomatik bağlama yeniden yönlendirme](how-to-enable-and-disable-automatic-binding-redirection.md).</span><span class="sxs-lookup"><span data-stu-id="c6c61-145">For information about how to turn this feature on or off, see [How to: Enable and Disable Automatic Binding Redirection](how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

<a name="bypass_PP"></a>

### <a name="bypassing-publisher-policy"></a><span data-ttu-id="c6c61-146">Yayımcı ilkesi atlanıyor</span><span class="sxs-lookup"><span data-stu-id="c6c61-146">Bypassing publisher policy</span></span>

 <span data-ttu-id="c6c61-147">Gerekirse, uygulama yapılandırma dosyasında yayımcı ilkesini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-147">You can override publisher policy in the app configuration file if necessary.</span></span> <span data-ttu-id="c6c61-148">Örneğin, geriye dönük olarak uyumlu olması talep eden derlemelerin yeni sürümleri de bir uygulamayı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-148">For example, new versions of assemblies that claim to be backward compatible can still break an app.</span></span> <span data-ttu-id="c6c61-149">Yayımcı ilkesini atlamak istiyorsanız, [\<publisherPolicy>](./file-schema/runtime/publisherpolicy-element.md) [\<dependentAssembly>](./file-schema/runtime/dependentassembly-element.md) uygulama yapılandırma dosyasındaki öğesine bir öğe ekleyin ve **Uygula** özniteliğini **Hayır**olarak ayarlayın. Bu, önceki tüm **Evet** ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c6c61-149">If you want to bypass publisher policy, add a [\<publisherPolicy>](./file-schema/runtime/publisherpolicy-element.md) element to the [\<dependentAssembly>](./file-schema/runtime/dependentassembly-element.md) element in the app configuration file, and set the **apply** attribute to **no**, which overrides any previous **yes** settings.</span></span>

 `<publisherPolicy apply="no" />`

 <span data-ttu-id="c6c61-150">Uygulamanızı kullanıcılarınız için çalıştırmaya devam etmek için yayımcı ilkesini atlayın, ancak sorunu derleme satıcısına bildirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6c61-150">Bypass publisher policy to keep your app running for your users, but make sure you report the problem to the assembly vendor.</span></span> <span data-ttu-id="c6c61-151">Bir derlemenin yayımcı ilke dosyası varsa, satıcı derlemenin geriye dönük olarak uyumlu olduğundan ve istemcilerin yeni sürümü mümkün olduğunca kullanabilmesini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6c61-151">If an assembly has a publisher policy file, the vendor should make sure that the assembly is backward compatible and that clients can use the new version as much as possible.</span></span>

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>

## <a name="redirecting-assembly-versions-at-the-machine-level"></a><span data-ttu-id="c6c61-152">Makine düzeyinde derleme sürümlerini yeniden yönlendirme</span><span class="sxs-lookup"><span data-stu-id="c6c61-152">Redirecting assembly versions at the machine level</span></span>

 <span data-ttu-id="c6c61-153">Bir makine yöneticisi bir bilgisayardaki tüm uygulamaların belirli bir derleme sürümünü kullanmasını istediğinde nadir durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-153">There might be rare cases when a machine administrator wants all apps on a computer to use a specific version of an assembly.</span></span> <span data-ttu-id="c6c61-154">Örneğin, yönetici her uygulamanın belirli bir derleme sürümünü kullanmasını isteyebilir, çünkü bu sürüm bir güvenlik deliği düzeltir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-154">For example, the administrator might want every app to use a particular assembly version, because that version fixes a security hole.</span></span> <span data-ttu-id="c6c61-155">Bir derleme makinenin yapılandırma dosyasında yeniden yönlendirilirse, eski sürümü kullanan bu makinede bulunan tüm uygulamalar yeni sürümü kullanmak üzere yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-155">If an assembly is redirected in the machine's configuration file, all apps on that machine that use the old version will be directed to use the new version.</span></span> <span data-ttu-id="c6c61-156">Makine yapılandırma dosyası, uygulama yapılandırma dosyasını ve yayımcı ilkesi dosyasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c6c61-156">The machine configuration file overrides the app configuration file and the publisher policy file.</span></span> <span data-ttu-id="c6c61-157">Bu dosya%*Runtime Install Path*% \ config dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c6c61-157">This file is located in the %*runtime install path*%\Config directory.</span></span> <span data-ttu-id="c6c61-158">Genellikle, .NET Framework%drive%\Windows\Microsoft.NET\Framework dizinine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-158">Typically, the .NET Framework is installed in the %drive%\Windows\Microsoft.NET\Framework directory.</span></span>

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>

## <a name="specifying-assembly-binding-in-configuration-files"></a><span data-ttu-id="c6c61-159">Yapılandırma dosyalarında bütünleştirilmiş kod bağlamayı belirtme</span><span class="sxs-lookup"><span data-stu-id="c6c61-159">Specifying assembly binding in configuration files</span></span>

 <span data-ttu-id="c6c61-160">Uygulama yapılandırma dosyasında, makine yapılandırma dosyasında veya yayımcı ilke dosyasında olup olmadığı gibi bağlama yeniden yönlendirmeleri belirtmek için aynı XML biçimini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c6c61-160">You use the same XML format to specify binding redirects whether it’s in the app configuration file, the machine configuration file, or the publisher policy file.</span></span> <span data-ttu-id="c6c61-161">Bir derleme sürümünü diğerine yeniden yönlendirmek için [\<bindingRedirect>](./file-schema/runtime/bindingredirect-element.md) öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6c61-161">To redirect one assembly version to another, use the [\<bindingRedirect>](./file-schema/runtime/bindingredirect-element.md) element.</span></span> <span data-ttu-id="c6c61-162">**OldVersion** özniteliği tek bir derleme sürümü veya bir dizi sürüm belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-162">The **oldVersion** attribute can specify a single assembly version or a range of versions.</span></span> <span data-ttu-id="c6c61-163">`newVersion`Öznitelik tek bir sürüm belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-163">The `newVersion` attribute should specify a single version.</span></span>  <span data-ttu-id="c6c61-164">Örneğin, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` çalışma zamanının 1.1.0.0 ve 1.2.0.0 arasındaki derleme sürümleri yerine 2.0.0.0 sürümünü kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-164">For example, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` specifies that the runtime should use version 2.0.0.0 instead of the assembly versions between 1.1.0.0 and 1.2.0.0.</span></span>

 <span data-ttu-id="c6c61-165">Aşağıdaki kod örneğinde çeşitli bağlama yeniden yönlendirme senaryoları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-165">The following code example demonstrates a variety of binding redirect scenarios.</span></span> <span data-ttu-id="c6c61-166">Örnek, için bir dizi sürüm için yeniden yönlendirme `myAssembly` ve için tek bir bağlama yeniden yönlendirme belirtir `mySecondAssembly` .</span><span class="sxs-lookup"><span data-stu-id="c6c61-166">The example specifies a redirect for a range of versions for `myAssembly`, and a single binding redirect for `mySecondAssembly`.</span></span> <span data-ttu-id="c6c61-167">Örnek ayrıca yayımcı ilke dosyasının için bağlama yeniden yönlendirmelerini geçersiz kılmayacağını belirtir `myThirdAssembly` .</span><span class="sxs-lookup"><span data-stu-id="c6c61-167">The example also specifies that publisher policy file will not override the binding redirects for `myThirdAssembly`.</span></span>

 <span data-ttu-id="c6c61-168">Bir derlemeyi bağlamak için, etiketindeki **xmlns** özniteliğiyle birlikte "urn: schemas-microsoft-com: asm. v1" dizesini belirtmeniz gerekir [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) .</span><span class="sxs-lookup"><span data-stu-id="c6c61-168">To bind an assembly, you must specify the string "urn:schemas-microsoft-com:asm.v1" with the **xmlns** attribute in the [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) tag.</span></span>

```xml
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="myAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
        <!-- Assembly versions can be redirected in app,
          publisher policy, or machine configuration files. -->
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
        <assemblyIdentity name="mySecondAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
      <assemblyIdentity name="myThirdAssembly"
        publicKeyToken="32ab4ba45e0a69a1"
        culture="en-us" />
        <!-- Publisher policy can be set only in the app
          configuration file. -->
        <publisherPolicy apply="no" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

### <a name="limiting-assembly--bindings-to-a-specific-version"></a><span data-ttu-id="c6c61-169">Derleme bağlamalarını belirli bir sürümle sınırlandırma</span><span class="sxs-lookup"><span data-stu-id="c6c61-169">Limiting assembly  bindings to a specific version</span></span>

 <span data-ttu-id="c6c61-170">**appliesTo** [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) Derleme bağlama başvurularını .NET Framework belirli bir sürümüne yönlendirmek için bir uygulama yapılandırma dosyasında öğesinde AppliesTo özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-170">You can use the **appliesTo** attribute on the [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element in an app configuration file to redirect assembly binding references to a specific version of the .NET Framework.</span></span> <span data-ttu-id="c6c61-171">Bu isteğe bağlı öznitelik, hangi sürümün uygulanacağını göstermek için .NET Framework bir sürüm numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6c61-171">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="c6c61-172">Hiçbir **AppliesTo** özniteliği belirtilmemişse, [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) öğesi .NET Framework tüm sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-172">If no **appliesTo** attribute is specified, the [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element applies to all versions of the .NET Framework.</span></span>

 <span data-ttu-id="c6c61-173">Örneğin, bir .NET Framework 3,5 derlemesi için derleme bağlamayı yeniden yönlendirmek için, uygulama yapılandırma dosyanıza aşağıdaki XML kodunu dahil edersiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-173">For example, to redirect assembly binding for a .NET Framework 3.5 assembly, you would include the following XML code in your app configuration file.</span></span>

```xml
<runtime>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"
    appliesTo="v3.5">
    <dependentAssembly>
      <!-- assembly information goes here -->
    </dependentAssembly>
  </assemblyBinding>
</runtime>
```

 <span data-ttu-id="c6c61-174">Yeniden yönlendirme bilgilerini sürüm sırasına girmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6c61-174">You should enter redirection information in version order.</span></span> <span data-ttu-id="c6c61-175">Örneğin, .NET Framework 3,5 derlemeleri için derleme bağlama yeniden yönlendirme bilgilerini ve ardından .NET Framework 4,5 derlemelerini girin.</span><span class="sxs-lookup"><span data-stu-id="c6c61-175">For example, enter assembly binding redirection information for .NET Framework 3.5 assemblies followed by .NET Framework 4.5 assemblies.</span></span> <span data-ttu-id="c6c61-176">Son olarak, **AppliesTo** özniteliğini kullanmayan ve bu nedenle .NET Framework tüm sürümleri için geçerli olan tüm .NET Framework bütünleştirilmiş kod yönlendirmesi için derleme bağlama yeniden yönlendirme bilgilerini girin.</span><span class="sxs-lookup"><span data-stu-id="c6c61-176">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="c6c61-177">Yeniden yönlendirmede bir çakışma varsa, yapılandırma dosyasındaki ilk eşleşen yeniden yönlendirme ekstresi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6c61-177">If there is a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>

 <span data-ttu-id="c6c61-178">Örneğin, bir .NET Framework 3,5 derlemesine bir başvuruyu ve .NET Framework 4 derlemesine başka bir başvuruyu yeniden yönlendirmek için aşağıdaki sözde kodda gösterilen kalıbı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6c61-178">For example, to redirect one reference to a .NET Framework 3.5 assembly and another reference to a .NET Framework 4 assembly, use the pattern shown in the following pseudocode.</span></span>

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a><span data-ttu-id="c6c61-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6c61-179">See also</span></span>

- [<span data-ttu-id="c6c61-180">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="c6c61-180">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="c6c61-181">\<bindingRedirect> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="c6c61-181">\<bindingRedirect> Element</span></span>](./file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="c6c61-182">Derleme Bağlama Yönlendirmesi Güvenlik İzni</span><span class="sxs-lookup"><span data-stu-id="c6c61-182">Assembly Binding Redirection Security Permission</span></span>](assembly-binding-redirection-security-permission.md)
- [<span data-ttu-id="c6c61-183">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="c6c61-183">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="c6c61-184">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="c6c61-184">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="c6c61-185">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="c6c61-185">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c6c61-186">Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c6c61-186">Configuring Apps</span></span>](index.md)
- [<span data-ttu-id="c6c61-187">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="c6c61-187">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="c6c61-188">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="c6c61-188">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="c6c61-189">Nasıl yapılır: Yayımcı İlkesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6c61-189">How to: Create a Publisher Policy</span></span>](how-to-create-a-publisher-policy.md)
