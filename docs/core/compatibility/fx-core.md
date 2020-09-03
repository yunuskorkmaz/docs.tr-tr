---
title: Son değişiklikler-.NET Core 'a .NET Framework
titleSuffix: ''
description: .NET Framework 'den .NET Core 'a yapılan son değişiklikleri listeler.
ms.date: 05/05/2020
ms.openlocfilehash: e9fa37dba89bbd6c4829614c27cb66206069fa9b
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414467"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="b8e31-103">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="b8e31-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="b8e31-104">.NET Framework bir uygulamayı .NET Core 'a geçiriyorsanız, bu makalede listelenen son değişiklikler sizi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b8e31-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="b8e31-105">Son değişiklikler, eklenen .NET Core sürümüne göre kategoriye ve bu kategorilerin içine göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="b8e31-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="b8e31-106">Bu makale, .NET Framework ve .NET Core arasındaki önemli değişikliklerden oluşan bir liste değildir.</span><span class="sxs-lookup"><span data-stu-id="b8e31-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="b8e31-107">Bunlara göz önünde bulundurulduğumuz için en önemli son değişiklikler buraya eklenir.</span><span class="sxs-lookup"><span data-stu-id="b8e31-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="b8e31-108">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="b8e31-108">Core .NET libraries</span></span>

- [<span data-ttu-id="b8e31-109">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="b8e31-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="b8e31-110">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="b8e31-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [<span data-ttu-id="b8e31-111">Bozuk işlem durumu özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-111">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported)
- [<span data-ttu-id="b8e31-112">UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz</span><span class="sxs-lookup"><span data-stu-id="b8e31-112">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters)
- [<span data-ttu-id="b8e31-113">Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="b8e31-113">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start)

### <a name="net-core-21"></a><span data-ttu-id="b8e31-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b8e31-114">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="b8e31-115">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="b8e31-115">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***

## <a name="cryptography"></a><span data-ttu-id="b8e31-116">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="b8e31-116">Cryptography</span></span>

- [<span data-ttu-id="b8e31-117">SignedCms. ComputeSignature Boolean parametresi dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="b8e31-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="b8e31-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b8e31-118">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="msbuild"></a><span data-ttu-id="b8e31-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="b8e31-119">MSBuild</span></span>

- [<span data-ttu-id="b8e31-120">Kaynak bildirimi dosya adı değişikliği</span><span class="sxs-lookup"><span data-stu-id="b8e31-120">Resource manifest file name change</span></span>](#resource-manifest-file-name-change)

### <a name="net-core-30"></a><span data-ttu-id="b8e31-121">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b8e31-121">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="networking"></a><span data-ttu-id="b8e31-122">Ağ</span><span class="sxs-lookup"><span data-stu-id="b8e31-122">Networking</span></span>

- [<span data-ttu-id="b8e31-123">WebClient. Iptallasync her zaman hemen iptal etmez</span><span class="sxs-lookup"><span data-stu-id="b8e31-123">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately)
- [<span data-ttu-id="b8e31-124">Tanımlama bilgisi yol işleme artık RFC 6265 ' e uyar</span><span class="sxs-lookup"><span data-stu-id="b8e31-124">Cookie Path handling now conforms to RFC 6265</span></span>](#cookie-path-handling-now-conforms-to-rfc-6265)

### <a name="net-core-20"></a><span data-ttu-id="b8e31-125">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b8e31-125">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***

### <a name="net-50"></a><span data-ttu-id="b8e31-126">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="b8e31-126">.NET 5.0</span></span>

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="b8e31-127">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8e31-127">Windows Forms</span></span>

<span data-ttu-id="b8e31-128">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b8e31-128">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="b8e31-129">.NET Framework bir Windows Forms uygulamasını .NET Core 'a geçiriyorsanız, burada listelenen son değişiklikler uygulamanızı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b8e31-129">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="b8e31-130">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="b8e31-130">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="b8e31-131">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="b8e31-131">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="b8e31-132">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="b8e31-132">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="b8e31-133">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="b8e31-133">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="b8e31-134">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b8e31-134">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="b8e31-135">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-135">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="b8e31-136">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-136">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="b8e31-137">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-137">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="b8e31-138">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-138">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="b8e31-139">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-139">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="b8e31-140">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-140">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="b8e31-141">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-141">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="b8e31-142">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-142">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)

### <a name="net-core-31"></a><span data-ttu-id="b8e31-143">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b8e31-143">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="b8e31-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b8e31-144">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9 pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

## <a name="see-also"></a><span data-ttu-id="b8e31-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8e31-145">See also</span></span>

- [<span data-ttu-id="b8e31-146">.NET Core üzerinde her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="b8e31-146">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="b8e31-147">.NET Core 'da .NET Framework teknolojileri kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="b8e31-147">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
