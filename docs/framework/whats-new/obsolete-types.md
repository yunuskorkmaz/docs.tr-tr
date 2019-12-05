---
title: .NET Framework eski türler
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
ms.openlocfilehash: b7932a553f39e1f1da2a3946878d6224099da8da
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802693"
---
# <a name="obsolete-types-in-the-net-framework"></a>.NET Framework eski türler

<a name="introduction"></a>Bu makaledeki tablolarda, derleme tarafından düzenlenen .NET Framework 4,5 ve .NET Framework 4,6 ' de kullanılmayan türler listelenmektedir. Eski türlerin bir listesini ve her derlemede önerilen alternatifleri görmek için aşağıdaki bağlantıları kullanın. Bu türler artık kullanılmıyor olduğundan, tüm üyeleri de artık kullanılmıyor. .NET Framework sınıf kitaplığındaki eski ek üyelerin listesi için, bkz. [Eski Üyeler](obsolete-members.md).

- [Sistem derlemelerinde eski türler](#obsolete_types_in_system_assemblies)

  - [mscorlib.dll](#mscorlib)

  - [System. Core. dll](#Core)

  - [System. Data. dll](#data)

  - [System.Data.OracleClient.dll](#oracleclient)

  - [System. Design. dll](#design)

  - [System.dll](#system)

  - [System.EnterpriseServices.dll](#enterpriseservices)

  - [System.Net.dll](#net)

  - [System.ServiceModel.dll](#servicemodel)

  - [System. Web. dll](#web)

  - [System.Web.Mobile.dll](#mobile)

  - [System. Workflow. Activities. dll](#workflow_activities)

  - [System. Workflow. ComponentModel. dll](#workflow_componentmodel)

  - [System. Workflow. Runtime. dll](#workflow_runtime)

  - [System. WorkflowServices. dll](#workflowservices)

  - [System.Xaml.dll](#xaml)

  - [System.Xml.dll](#xml)

  - [WindowsBase.dll](#WindowsBase)

- [Microsoft Derlemelerindeki Eski türler](#obsolete_types_in_microsoft_assemblies)

  - [IEHost. dll ve IEExec. exe](#IEHost)

  - [Microsoft.Build.Engine.dll](#Engine)

  - [Microsoft.JScript.dll](#jscript)

  - [Microsoft. VisualBasic. Compatibility. dll](#VBCompat)

  - [Microsoft. VisualBasic. Compatibility. Data. dll](#VBCompatData)

  - [Microsoft.VisualC.dll](#visualc)

<a name="obsolete_types_in_system_assemblies"></a>

## <a name="obsolete-types-in-system-assemblies"></a>Sistem derlemelerinde eski türler

Aşağıdaki tablolarda sistem derlemelerinde Kullanımdan kaldırılmış olarak belirtilen türler listelenmektedir. Bu derlemeler, .NET Framework hedefleyen genel\-amacı uygulama geliştirmesi için kullanılır.

<a name="mscorlib"></a>

### <a name="assembly-mscorlibdll"></a>Bütünleştirilmiş kod: mscorlib. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|Bu tür, daha önce çalışma zamanında belirtilmeyen bir önemli hatayı belirtti. Çalışma zamanı artık bu özel durumu harekete geçirmeyecek, bu nedenle bu tür kullanılmıyor.|
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|Lütfen bunun yerine <xref:System.StringComparer?displayProperty=nameWithType> kullanın.|
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|Lütfen bunun yerine <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType> kullanın.|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash> sınıfı kullanım dışı bırakıldı.|
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı. Bunun yerine System. Runtime. CompilerServices ad alanındaki <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> sınıfını kullanın.|
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=nameWithType>|Alternatif bir API kullanılabilir: bunun yerine <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> özel özniteliğini yay.|
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
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|Bu öznitelik kullanım dışıdır ve gelecek bir sürümde kaldırılacak.|
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> kullanım dışıdır.|
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType> kullanın.|
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|Bu öznitelik kullanım dışı bırakıldı. Uygulama etki alanları, IDispatch çağrılarında artık etkinleştirme bağlam sınırlarına uymaz.|
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
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope> yalnızca .NET 2,0 saydamlık uyumluluğu için kullanılır.|
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute> yalnızca .NET 2,0 saydamlık uyumluluğu için kullanılır. Lütfen bunun yerine <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType> kullanın.|
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|Bu tür kullanımdan kalkmıştır ve .NET Framework gelecek bir sürümünde kaldırılacaktır.|
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|Derleme düzeyinde bildirime dayalı güvenlik artık kullanılmıyor ve varsayılan olarak CLR tarafından uygulanmıyor.|
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|Bu tür kullanımdan kalkmıştır ve .NET Framework gelecek bir sürümünde kaldırılacaktır.|

[Başa dön](#introduction)

<a name="Core"></a>

### <a name="assembly-systemcoredll"></a>Bütünleştirilmiş kod: System. Core. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu türü kullanmayın.|

[Başa dön](#introduction)

<a name="data"></a>

### <a name="assembly-systemdatadll"></a>Bütünleştirilmiş kod: System. Data. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute> kullanım dışı bırakıldı.|
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes> kullanım dışı bırakıldı.|
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|<xref:System.Data.TypedDataSetGenerator> sınıfı gelecek bir sürümde kaldırılacak. Lütfen System. Design. dll içinde <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType> kullanın.|
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|<xref:System.Xml.XmlDataDocument> sınıfı gelecek bir sürümde kaldırılacak.|

[Başa dön](#introduction)

<a name="oracleclient"></a>

### <a name="assembly-systemdataoracleclientdll"></a>Bütünleştirilmiş kod: System. Data. OracleClient. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleClientFactory> kullanım dışı bırakıldı.|
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommand> kullanım dışı bırakıldı.|
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommandBuilder> kullanım dışı bırakıldı.|
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnection> kullanım dışı bırakıldı.|
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder> kullanım dışı bırakıldı.|
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleDataAdapter> kullanım dışı bırakıldı.|
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermission> kullanım dışı bırakıldı.|
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType> kullanım dışı bırakıldı.|

[Başa dön](#introduction)

<a name="design"></a>

### <a name="assembly-systemdesigndll"></a>Bütünleştirilmiş kod: System. Design. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Bunun yerine <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType> kullanın.|
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|Bu türün kullanılması önerilmez çünkü DataBindings düzenlemesi, özellik Kılavuzu yerine bir <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> ile başlatılır.|
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|Bu türün kullanılması önerilmez çünkü DataBindings düzenlemesi, özellik Kılavuzu yerine bir <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> ile başlatılır.|
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> ve <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> ve <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|Şablon düzenlemesi <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>içinde işlendiği için bu tür kullanılması önerilmez. Şablon düzenlemesini desteklemek için <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> özelliğindeki şablon verilerini kullanıma sunun ve <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>çağırın.|
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsReferenceManager> ek işlevsellik içerir ve daha fazla genişletilebilirlik sağlar. <xref:System.Web.UI.Design.WebFormsReferenceManager>almak için <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>`RootDesigner.ReferenceManager` özelliğini kullanın.|
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsRootDesigner> ek işlevsellik içerir ve daha fazla genişletilebilirlik sağlar. <xref:System.Web.UI.Design.WebFormsRootDesigner>almak için <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType><xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> özelliğini kullanın.|
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|Şablon düzenlemesi <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>içinde işlendiği için bu tür kullanılması önerilmez. Şablon düzenlemesini desteklemek için <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> özelliğindeki şablon verilerini kullanıma sunun ve <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>çağırın.|
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|İçeriğin düzenlenmesine yönelik bir <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> kullandığından Önerilen alternatif <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType>. Tasarımcı bölgeleri, düzenlenmekte olan içeriğin daha iyi denetime izin verir.|
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|Şablon düzenlemesi <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>içinde işlendiği için bu tür kullanılması önerilmez. Şablon düzenlemesini desteklemek için <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> özelliğindeki şablon verilerini kullanıma sunun ve <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>çağırın.|
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|Şablon düzenlemesi <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>içinde işlendiği için bu tür kullanılması önerilmez. Şablon düzenlemesini desteklemek için <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> özelliğindeki şablon verilerini kullanıma sunun ve <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>çağırın.|
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|Otomatik biçimlendirme iletişim kutusu Tasarımcı ana bilgisayarı tarafından başlatıldığından bu türün kullanılması önerilmez. Kullanılabilir otomatik biçimlerin listesi, <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> özelliğindeki <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> gösterilir.|
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|İçeriğin düzenlenmesine yönelik bir <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> kullandığından Önerilen alternatif <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType>. Tasarımcı bölgeleri, düzenlenmekte olan içeriğin daha iyi denetime izin verir.|

[Başa dön](#introduction)

<a name="system"></a>

### <a name="assembly-systemdll"></a>Bütünleştirilmiş kod: System. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|Bu arabirim kullanım dışı bırakıldı. Bunun yerine <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType> tür işlemek için <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> ekleyin.|
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|Yeni ayarlar modeliyle çalışmak için <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> kullanın.|
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|Bu öznitelik kullanım dışı bırakıldı. Bunun yerine <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType> kullanın.|
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı.|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Bunun yerine <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> sınıfı aracılığıyla performans sayaçlarını kullanın.|
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Lütfen genel varsayılan proxy 'yi erişmek ve ayarlamak için <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> kullanın. <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>yerine ' null ' kullanın.|
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|

[Başa dön](#introduction)

<a name="enterpriseservices"></a>

### <a name="assembly-systementerpriseservicesdll"></a>Bütünleştirilmiş kod: System. EnterpriseServices. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|<xref:System.EnterpriseServices.RegistrationHelperTx> sınıfı kullanım dışı bırakıldı.|

[Başa dön](#introduction)

<a name="net"></a>

### <a name="assembly-systemnetdll"></a>Bütünleştirilmiş kod: System. net. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|

[Başa dön](#introduction)

<a name="servicemodel"></a>

### <a name="assembly-systemservicemodeldll"></a>Bütünleştirilmiş kod: System. ServiceModel. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Eş Kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu tür artık kullanılmıyor. Http <xref:System.Net.CookieContainer>etkinleştirmek için, http bağlamasındaki veya <xref:System.ServiceModel.Channels.HttpTransportBindingElement>`AllowCookies` özelliğini kullanın.|
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Eş Kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Eş Kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Eş Kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Eş Kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Eş Kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Eş Kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|

[Başa dön](#introduction)

<a name="web"></a>

### <a name="assembly-systemwebdll"></a>Bütünleştirilmiş kod: System. Web. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|Bu tür artık kullanılmıyor. Passport kimlik doğrulama ürünü artık desteklenmiyor ve [Microsoft hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından değiştirildi|
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>.|
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|Bu tür artık kullanılmıyor. Passport kimlik doğrulama ürünü artık desteklenmiyor ve [Microsoft hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından değiştirildi|
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|Bu tür artık kullanılmıyor. Passport kimlik doğrulama ürünü artık desteklenmiyor ve [Microsoft hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından değiştirildi|
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|Bu tür artık kullanılmıyor. Passport kimlik doğrulama ürünü artık desteklenmiyor ve [Microsoft hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından değiştirildi|
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|Bu tür artık kullanılmıyor. Passport kimlik doğrulama ürünü artık desteklenmiyor ve [Microsoft hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından değiştirildi|
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|Bu tür artık kullanılmıyor. Passport kimlik doğrulama ürünü artık desteklenmiyor ve [Microsoft hesabı](https://account.microsoft.com/account/Account?destrt=home-index) tarafından değiştirildi|
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Convert?displayProperty=nameWithType> ve <xref:System.String.Format%2A?displayProperty=nameWithType>.|

[Başa dön](#introduction)

<a name="mobile"></a>

### <a name="assembly-systemwebmobiledll"></a>Bütünleştirilmiş kod: System. Web. Mobile. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|System. Web. Mobile. dll derlemesi kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. ASP.NET mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Mobiles için ASP.net](/aspnet/mobile/overview).|

[Başa dön](#introduction)

<a name="workflow_activities"></a>

### <a name="assembly-systemworkflowactivitiesdll"></a>Bütünleştirilmiş kod: System. Workflow. Activities. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Workflow.Activities?displayProperty=nameWithType> ad alanındaki tüm türler|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|

[Başa dön](#introduction)

<a name="workflow_componentmodel"></a>

### <a name="assembly-systemworkflowcomponentmodeldll"></a>Bütünleştirilmiş kod: System. Workflow. ComponentModel. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> ve <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType> hariç <xref:System.Workflow.ComponentModel> ad alanındaki tüm türler|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> ve <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType> hariç <xref:System.Workflow.ComponentModel.Compiler> ad alanındaki tüm türler|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.ComponentModel.Design> ad alanındaki tüm türler <xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler> hariç|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|

[Başa dön](#introduction)

<a name="workflow_runtime"></a>

### <a name="assembly-systemworkflowruntimedll"></a>Bütünleştirilmiş kod: System. Workflow. Runtime. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Activities.Statements.Interop?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br />Workflow Foundation 3,0 türleri kullanım dışıdır. Bunun yerine, <xref:System.Activities>Iş akışı 4,0 türlerini kullanın.\*.|
|<xref:System.Activities.Tracking.InteropTrackingRecord?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br />Workflow Foundation 3,0 türleri kullanım dışıdır. Bunun yerine, <xref:System.Activities>Iş akışı 4,0 türlerini kullanın.\*.|
|<xref:System.Workflow.Runtime> ad alanındaki tüm türler|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.Runtime.Configuration> ad alanındaki tüm türler|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.Runtime.DebugEngine> ad alanındaki tüm türler <xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback> hariç|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.Runtime.Hosting> ad alanındaki tüm türler <xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback> hariç|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|
|<xref:System.Workflow.Runtime.Tracking> ad alanındaki tüm türler|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> System. Workflow.\* türler kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni türleri kullanın.\*.|

[Başa dön](#introduction)

<a name="workflowservices"></a>

### <a name="assembly-systemworkflowservicesdll"></a>Bütünleştirilmiş kod: System. WorkflowServices. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.Workflow.Activities?displayProperty=nameWithType> ad alanındaki tüm türler|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> WF 3 türleri kullanım dışıdır. Bunun yerine, lütfen <xref:System.Activities>yeni WF 4 türlerini kullanın.\*.|

[Başa dön](#introduction)

<a name="xaml"></a>

### <a name="assembly-systemxamldll"></a>Bütünleştirilmiş kod: System. xaml. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|Bu, XAML ayrıştırıcısı tarafından kullanılmaz. Lütfen <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>bakın.|

[Başa dön](#introduction)

<a name="xml"></a>

### <a name="assembly-systemxmldll"></a>Bütünleştirilmiş kod: System. xml. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|.NET Framework 4,5 ' de ilk kullanım dışı.<br /><br /> Bu türün kullanımı bir derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|Şema derleme ve doğrulama için <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> kullanın.|
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|Yerine uygun <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType> kullanarak <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> yöntemi tarafından oluşturulan bir <xref:System.Xml.XmlReader?displayProperty=nameWithType> kullanın.|
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|Bu türün kullanımı bir derleyici hatası oluşturur. Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Lütfen bunun yerine <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType> kullanın.|

[Başa dön](#introduction)

<a name="WindowsBase"></a>

### <a name="assembly-windowsbasedll"></a>Bütünleştirilmiş kod: WindowsBase. dll

|Tür|İleti|
|----------|-------------|
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType> kullanım dışı bırakıldı. Bu arabirim artık kullanımda değil.|

[Başa dön](#introduction)

<a name="obsolete_types_in_microsoft_assemblies"></a>

## <a name="obsolete-types-in-microsoft-assemblies"></a>Microsoft Derlemelerindeki Eski türler

Aşağıdaki bölümlerde, Microsoft Derlemelerindeki Eski türler listelenmektedir. Bu derlemeler, tek bir dili hedefleyen derlemeler (örneğin, Microsoft. JScript. dll veya Microsoft. VisualC. dll) gibi özel amaçlı derlemelerdir.

<a name="IEHost"></a>

### <a name="assembly-iehostdll-and-ieexecexe"></a>Bütünleştirilmiş kod: IEHost. dll ve IEExec. exe

IEHost. dll ve IEExec. exe derlemeleri .NET Framework kaldırılmıştır. Tüm türleri ve üyeleri artık kullanılmıyor ve .NET Framework 4 itibariyle desteklenmez. Bu derlemeler Windows Forms denetimlerini barındırmak ve Internet Explorer 'da yürütülebilir dosyaları çalıştırmak için kullanıldı. Önerilen alternatifler ClickOnce, XAML tarayıcı uygulamaları (XBAP) ve Microsoft Silverlight içerir.

[Başa dön](#introduction)

<a name="Engine"></a>

### <a name="assembly-microsoftbuildenginedll"></a>Bütünleştirilmiş kod: Microsoft. Build. Engine. dll

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Lütfen bunun yerine *Microsoft. Build* derlemesinden <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> kullanın.|
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Lütfen bunun yerine *Microsoft. Build* derlemesinden <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> kullanın.|

[Başa dön](#introduction)

<a name="jscript"></a>

### <a name="assembly-microsoftjscriptdll"></a>Bütünleştirilmiş kod: Microsoft. JScript. dll

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|Bu tür, Visual Studio 2005 ' de kullanımdan kaldırılmıştır; Bu özellik için bir değişiklik yoktur. Ek Yardım için lütfen <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> belgelerine bakın.|

[Başa dön](#introduction)

<a name="VBCompat"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>Bütünleştirilmiş kod: Microsoft. VisualBasic. Compatibility. dll

Visual Basic 6 ' dan geçirme hakkında daha fazla bilgi için, bkz. [Visual Basic 6,0 Kaynak Merkezi](https://docs.microsoft.com/previous-versions/visualstudio/visual-basic-6/visual-basic-6.0-documentation).

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|

[Başa dön](#introduction)

<a name="VBCompatData"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>Bütünleştirilmiş kod: Microsoft. VisualBasic. Compatibility. Data. dll

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=nameWithType>|Bu üye artık kullanılmıyor.|

[Başa dön](#introduction)

<a name="visualc"></a>

### <a name="assembly-microsoftvisualcdll"></a>Bütünleştirilmiş kod: Microsoft. VisualC. dll

|Tür|İleti|
|----------|-------------|
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft. VisualC. dll eski bir derlemedir ve yalnızca geriye dönük uyumluluk için mevcuttur.|

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıf Kitaplığında Artık Kullanılmayanlar](whats-obsolete.md)
- [Eski Üyeler](obsolete-members.md)
