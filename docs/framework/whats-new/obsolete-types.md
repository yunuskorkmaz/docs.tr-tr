---
title: .NET Çerçevesinde Eski Türler
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
ms.openlocfilehash: b7932a553f39e1f1da2a3946878d6224099da8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802693"
---
# <a name="obsolete-types-in-the-net-framework"></a>.NET Çerçevesinde Eski Türler

<a name="introduction"></a>Bu makaledeki tablolar,.NET Framework 4.5'te ve derleme tarafından düzenlenen .NET Framework 4.6'da eskimiş türleri listelemaktadır. Eski türlerin ve her derlemede önerilen alternatiflerin listesini görmek için aşağıdaki bağlantıları kullanın. Bu türler eski olduğundan, tüm üyeleri de geçersizdir. .NET Framework sınıf kitaplığındaki eski üye listesi için [bkz.](obsolete-members.md)

- [Sistem montajlarında eski tipler](#obsolete_types_in_system_assemblies)

  - [mscorlib.dll](#mscorlib)

  - [System.Core.dll](#Core)

  - [System.Data.dll](#data)

  - [System.Data.OracleClient.dll](#oracleclient)

  - [Sistem.Design.dll](#design)

  - [System.dll](#system)

  - [System.EnterpriseServices.dll](#enterpriseservices)

  - [System.Net.dll](#net)

  - [System.ServiceModel.dll](#servicemodel)

  - [Sistem.Web.dll](#web)

  - [Sistem.Web.Mobile.dll](#mobile)

  - [System.Workflow.Activities.dll](#workflow_activities)

  - [System.Workflow.ComponentModel.dll](#workflow_componentmodel)

  - [System.Workflow.Runtime.dll](#workflow_runtime)

  - [System.WorkflowServices.dll](#workflowservices)

  - [Sistem.Xaml.dll](#xaml)

  - [System.Xml.dll](#xml)

  - [WindowsBase.dll](#WindowsBase)

- [Microsoft derlemelerinde eski türler](#obsolete_types_in_microsoft_assemblies)

  - [IEHost.dll ve IEExec.exe](#IEHost)

  - [Microsoft.Build.Engine.dll](#Engine)

  - [Microsoft.JScript.dll](#jscript)

  - [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)

  - [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)

  - [Microsoft.VisualC.dll](#visualc)

<a name="obsolete_types_in_system_assemblies"></a>

## <a name="obsolete-types-in-system-assemblies"></a>Sistem Montajlarında Eski Türler

Aşağıdaki tablolar, sistem derlemelerinde geçersiz ilan edilen türleri listeletir. Bu derlemeler .NET\-Framework'u hedefleyen genel amaçlı uygulama geliştirme için kullanılır.

<a name="mscorlib"></a>

### <a name="assembly-mscorlibdll"></a>Montaj: mscorlib.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|Bu tür daha önce çalışma zamanında belirtilmemiş bir önemli hata belirtmişti. Çalışma süresi artık bu özel durum yükseltir, bu nedenle bu tür eski.|
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|Lütfen <xref:System.StringComparer?displayProperty=nameWithType> onun yerine kullanın.|
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|Lütfen <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType> onun yerine kullanın.|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|Sınıf <xref:System.Configuration.Assemblies.AssemblyHash> amortismana uğradı.|
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır. Bunun <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> yerine System.Runtime.CompilerServices ad alanında sınıfı kullanın.|
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=nameWithType>|Alternatif bir API kullanılabilir: Bunun <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> yerine özel öznitelik yontun.|
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|Bu öznitelik amortismana alınır ve gelecekteki bir sürümde kaldırılır.|
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|Bu <xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> küçümsüyor.|
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|Bu özellik amortismana alındı. Uygulama Etki Alanları artık IDispatch aramalarında Etkinleştirme Bağlamı sınırlarına saygı duymaz.|
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=nameWithType> kullanın.|
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope>yalnızca .NET 2.0 saydamlık uyumluluğu için kullanılır.|
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute>yalnızca .NET 2.0 saydamlık uyumluluğu için kullanılır. Lütfen <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType> onun yerine kullanın.|
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|Bu tür eskidir ve .NET Framework'ün gelecekteki sürümünde kaldırılır.|
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|Derleme düzeyi bildirim güvenliği geçersizdir ve artık CLR tarafından varsayılan olarak uygulanmaz.|
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|Bu tür eskidir ve .NET Framework'ün gelecekteki sürümünde kaldırılır.|

[Başa dön](#introduction)

<a name="Core"></a>

### <a name="assembly-systemcoredll"></a>Montaj: System.Core.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu türü kullanmayın.|

[Başa dön](#introduction)

<a name="data"></a>

### <a name="assembly-systemdatadll"></a>Montaj: System.Data.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute>amortismana hazır hale gelmiştir.|
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes>amortismana hazır hale gelmiştir.|
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|Sınıf <xref:System.Data.TypedDataSetGenerator> gelecekteki bir sürümde kaldırılır. Lütfen <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType> System.Design.dll'de kullanın.|
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|Sınıf <xref:System.Xml.XmlDataDocument> gelecekteki bir sürümde kaldırılır.|

[Başa dön](#introduction)

<a name="oracleclient"></a>

### <a name="assembly-systemdataoracleclientdll"></a>Montaj: System.Data.OracleClient.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleClientFactory>amortismana hazır hale gelmiştir.|
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommand>amortismana hazır hale gelmiştir.|
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommandBuilder>amortismana hazır hale gelmiştir.|
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnection>amortismana hazır hale gelmiştir.|
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder>amortismana hazır hale gelmiştir.|
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleDataAdapter>amortismana hazır hale gelmiştir.|
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermission>amortismana hazır hale gelmiştir.|
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>amortismana hazır hale gelmiştir.|

[Başa dön](#introduction)

<a name="design"></a>

### <a name="assembly-systemdesigndll"></a>Montaj: System.Design.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|Bu sınıf küçümsül. Bunun yerine <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType> kullanın.|
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|DataBindings düzenlemesi özellik ızgarası yerine bir <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> üzerinden başlatıldığı için bu tür kullanılması önerilmez.|
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|DataBindings düzenlemesi özellik ızgarası yerine bir <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> üzerinden başlatıldığı için bu tür kullanılması önerilmez.|
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> ve <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> ve <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|Şablon düzenleme ' de <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>işlendiğinden, bu türün kullanımı önerilmez. Şablon düzenlemeyi desteklemek için, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> şablon verilerini <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>özellikte gösterin ve çağırın.|
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>. Ek <xref:System.Web.UI.Design.WebFormsReferenceManager> işlevsellik içerir ve daha fazla genişletilebilirlik sağlar. Almak için <xref:System.Web.UI.Design.WebFormsReferenceManager>, `RootDesigner.ReferenceManager` sizin özelliği <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>kullanın.|
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>. Ek <xref:System.Web.UI.Design.WebFormsRootDesigner> işlevsellik içerir ve daha fazla genişletilebilirlik sağlar. Almak için <xref:System.Web.UI.Design.WebFormsRootDesigner>, <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> sizin özelliği <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>kullanın.|
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|Şablon düzenleme ' de <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>işlendiğinden, bu türün kullanımı önerilmez. Şablon düzenlemeyi desteklemek için, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> şablon verilerini <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>özellikte gösterin ve çağırın.|
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|Önerilen alternatif, <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType> içeriği düzenlemek <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> için bir kullanım olmasıdır. Tasarımcı bölgeleri, düzenlenen içeriğin daha iyi denetlemesine olanak sağlar.|
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|Şablon düzenleme ' de <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>işlendiğinden, bu türün kullanımı önerilmez. Şablon düzenlemeyi desteklemek için, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> şablon verilerini <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>özellikte gösterin ve çağırın.|
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|Şablon düzenleme ' de <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>işlendiğinden, bu türün kullanımı önerilmez. Şablon düzenlemeyi desteklemek için, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> şablon verilerini <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>özellikte gösterin ve çağırın.|
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|Otomatik Biçim iletişim kutusu tasarımcı ana bilgisayar tarafından başlatıldığı için bu tür kullanılması önerilmez. Kullanılabilir AutoFormat'ların listesi <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> özellikte açıklanır.|
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|Önerilen alternatif, <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType> içeriği düzenlemek <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> için bir kullanım olmasıdır. Tasarımcı bölgeleri, düzenlenen içeriğin daha iyi denetlemesine olanak sağlar.|

[Başa dön](#introduction)

<a name="system"></a>

### <a name="assembly-systemdll"></a>Montaj: System.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|Bu arayüz küçümsülse. Bunun <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> yerine işlemek <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType> için a ekleyin.|
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|Bunun <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> yerine yeni ayarlar modeli yle çalışmak için kullanın.|
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|Bu özellik amortismana alındı. Bunun yerine <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType> kullanın.|
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|Bu sınıf küçümsül.|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|Bu sınıf küçümsül. Bunun yerine <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> sınıf boyunca performans sayaçlarını kullanın.|
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|Bu sınıf küçümsül. Genel <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> varsayılan proxy'ye erişmek ve ayarlamak için lütfen bunun yerine kullanın. <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>'null' yerine 'null' kullanın.|
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|

[Başa dön](#introduction)

<a name="enterpriseservices"></a>

### <a name="assembly-systementerpriseservicesdll"></a>Montaj: System.EnterpriseServices.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|Sınıf <xref:System.EnterpriseServices.RegistrationHelperTx> amortismana uğradı.|

[Başa dön](#introduction)

<a name="net"></a>

### <a name="assembly-systemnetdll"></a>Montaj: System.Net.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|

[Başa dön](#introduction)

<a name="servicemodel"></a>

### <a name="assembly-systemservicemodeldll"></a>Montaj: System.ServiceModel.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Eş kanal özelliği eskidir ve gelecekte kaldırılır.|
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür eskidir. Http'yi <xref:System.Net.CookieContainer>etkinleştirmek `AllowCookies` için, Http bağlayıcısı <xref:System.ServiceModel.Channels.HttpTransportBindingElement>veya .|
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Eş kanal özelliği eskidir ve gelecekte kaldırılır.|
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Eş kanal özelliği eskidir ve gelecekte kaldırılır.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Eş kanal özelliği eskidir ve gelecekte kaldırılır.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Eş kanal özelliği eskidir ve gelecekte kaldırılır.|
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Eş kanal özelliği eskidir ve gelecekte kaldırılır.|
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Eş kanal özelliği eskidir ve gelecekte kaldırılır.|

[Başa dön](#introduction)

<a name="web"></a>

### <a name="assembly-systemwebdll"></a>Montaj: System.Web.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|Bu tür eskidir. Passport kimlik doğrulama ürünü artık desteklenmeyecek ve Microsoft [Hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından geçersiz sayıldı|
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>.|
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|Bu tür eskidir. Passport kimlik doğrulama ürünü artık desteklenmeyecek ve Microsoft [Hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından geçersiz sayıldı|
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|Bu tür eskidir. Passport kimlik doğrulama ürünü artık desteklenmeyecek ve Microsoft [Hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından geçersiz sayıldı|
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|Bu tür eskidir. Passport kimlik doğrulama ürünü artık desteklenmeyecek ve Microsoft [Hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından geçersiz sayıldı|
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|Bu tür eskidir. Passport kimlik doğrulama ürünü artık desteklenmeyecek ve Microsoft [Hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından geçersiz sayıldı|
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|Bu tür eskidir. Passport kimlik doğrulama ürünü artık desteklenmeyecek ve Microsoft [Hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından geçersiz sayıldı|
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Convert?displayProperty=nameWithType> ve <xref:System.String.Format%2A?displayProperty=nameWithType>.|

[Başa dön](#introduction)

<a name="mobile"></a>

### <a name="assembly-systemwebmobiledll"></a>Montaj: System.Web.Mobile.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll montajı amortismana alındı ve artık kullanılmamalıdır. Mobil uygulamalar ASP.NET nasıl geliştirilebilirsiniz hakkında bilgi [için, Cep Telefonları için ASP.NET'a](/aspnet/mobile/overview)bakın.|

[Başa dön](#introduction)

<a name="workflow_activities"></a>

### <a name="assembly-systemworkflowactivitiesdll"></a>Montaj: System.Workflow.Activities.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Workflow.Activities?displayProperty=nameWithType> Ad alanındaki tüm türler|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|

[Başa dön](#introduction)

<a name="workflow_componentmodel"></a>

### <a name="assembly-systemworkflowcomponentmodeldll"></a>Montaj: System.Workflow.ComponentModel.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Workflow.ComponentModel> Ad alanındaki tüm türler <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> hariç ve<xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.ComponentModel.Compiler> Ad alanındaki tüm türler <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> hariç ve<xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.ComponentModel.Design> Ad alanındaki tüm türler hariç<xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|

[Başa dön](#introduction)

<a name="workflow_runtime"></a>

### <a name="assembly-systemworkflowruntimedll"></a>Montaj: System.Workflow.Runtime.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Activities.Statements.Interop?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br />İş Akışı Temeli 3.0 türleri amortismana alınır. Bunun yerine, İş Akışı 4.0 türlerini <xref:System.Activities>kullanın. \*.|
|<xref:System.Activities.Tracking.InteropTrackingRecord?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br />İş Akışı Temeli 3.0 türleri amortismana alınır. Bunun yerine, İş Akışı 4.0 türlerini <xref:System.Activities>kullanın. \*.|
|<xref:System.Workflow.Runtime> Ad alanındaki tüm türler|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.Runtime.Configuration> Ad alanındaki tüm türler|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.Runtime.DebugEngine> Ad alanındaki tüm türler hariç<xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.Runtime.Hosting> Ad alanındaki tüm türler hariç<xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|
|<xref:System.Workflow.Runtime.Tracking> Ad alanındaki tüm türler|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> The System.Workflow. \* türleri amortismana alınır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın. \*.|

[Başa dön](#introduction)

<a name="workflowservices"></a>

### <a name="assembly-systemworkflowservicesdll"></a>Montaj: System.WorkflowServices.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.Workflow.Activities?displayProperty=nameWithType> Ad alanındaki tüm türler|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> WF 3 türleri amortismana alınır. Bunun yerine, lütfen yeni WF <xref:System.Activities>4 türlerini kullanın. \*.|

[Başa dön](#introduction)

<a name="xaml"></a>

### <a name="assembly-systemxamldll"></a>Montaj: System.Xaml.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|Bu XAML ayrıştırıcı tarafından kullanılmaz. Lütfen bak. <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>|

[Başa dön](#introduction)

<a name="xml"></a>

### <a name="assembly-systemxmldll"></a>Montaj: System.Xml.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|İlk olarak .NET Framework 4.5'te amortismana hazırdır.<br /><br /> Bu tür kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|Şema derleme ve doğrulama için kullanın. <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType>|
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|Uygun <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType> <xref:System.Xml.XmlReader?displayProperty=nameWithType> yerine kullanarak <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> yöntem tarafından oluşturulan bir kullanın.|
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|Bu tür kullanımı bir derleyici hatası oluşturur. Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|Bu sınıf küçümsül. Lütfen <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType> onun yerine kullanın.|

[Başa dön](#introduction)

<a name="WindowsBase"></a>

### <a name="assembly-windowsbasedll"></a>Derleme: WindowsBase.dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>amortismana hazır hale gelmiştir. Bu arabirim artık kullanılmıyor.|

[Başa dön](#introduction)

<a name="obsolete_types_in_microsoft_assemblies"></a>

## <a name="obsolete-types-in-microsoft-assemblies"></a>Microsoft Derlemelerinde Eski Türler

Aşağıdaki bölümlerde Microsoft derlemelerinde eski türleri listele. Bu derlemeler, tek bir dili hedefleyen derlemeler (örneğin, Microsoft.JScript.dll veya Microsoft.VisualC.dll) gibi özel amaçlı derlemelerdir.

<a name="IEHost"></a>

### <a name="assembly-iehostdll-and-ieexecexe"></a>Montaj: IEHost.dll ve IEExec.exe

IEHost.dll ve IEExec.exe derlemeleri .NET Framework kaldırıldı. Tüm türleri ve üyeleri geçersizdir ve .NET Framework 4 itibariyle desteklenmez. Bu derlemeler Windows Forms denetimlerini barındırmak ve Internet Explorer'da yürütülebilir leri çalıştırmak için kullanıldı. Önerilen alternatifler clickonce, XAML tarayıcı uygulamaları (XBAP) ve Microsoft Silverlight içerir.

[Başa dön](#introduction)

<a name="Engine"></a>

### <a name="assembly-microsoftbuildenginedll"></a>Derleme: Microsoft.Build.Engine.dll

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|Bu sınıf küçümsül. Bunun <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> yerine *Lütfen Microsoft.Build* derlemesinden kullanın.|
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|Bu sınıf küçümsül. Bunun <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> yerine *Lütfen Microsoft.Build* derlemesinden kullanın.|

[Başa dön](#introduction)

<a name="jscript"></a>

### <a name="assembly-microsoftjscriptdll"></a>Derleme: Microsoft.JScript.dll

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|Bu tür Visual Studio 2005 yılında amortismana uğradı; bu özelliğin yerine başka bir şey yoktur. Lütfen ek <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> yardım için belgelere bakın.|

[Başa dön](#introduction)

<a name="VBCompat"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>Derleme: Microsoft.VisualBasic.Compatibility.dll

Visual Basic 6'dan geçiş hakkında daha fazla bilgi için [Visual Basic 6.0 Kaynak Merkezi'ne](https://docs.microsoft.com/previous-versions/visualstudio/visual-basic-6/visual-basic-6.0-documentation)bakın.

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|

[Başa dön](#introduction)

<a name="VBCompatData"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>Derleme: Microsoft.VisualBasic.Compatibility.Data.dll

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=nameWithType>|Bu üye nin modası geçmiş.|

[Başa dön](#introduction)

<a name="visualc"></a>

### <a name="assembly-microsoftvisualcdll"></a>Derleme: Microsoft.VisualC.dll

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için vardır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıf Kitaplığı'nda Artık Kullanılmayanlar](whats-obsolete.md)
- [Eski Üyeler](obsolete-members.md)
