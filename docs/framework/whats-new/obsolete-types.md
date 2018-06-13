---
title: .NET Framework'teki eski türler
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5668292eaae2b05bbc056196a35a9b8840b7177
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508837"
---
# <a name="obsolete-types-in-the-net-framework"></a>.NET Framework'teki eski türler
<a name="introduction"></a> Bu makaledeki tablolar'te eski türler listesinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], derleme tarafından düzenlenir. Eski türler ve her derlemesindeki önerilen Alternatiflerle listesini görmek için aşağıdaki bağlantıları kullanın. Bu tür geçersiz olduğundan, tüm üyeleri aynı zamanda artık kullanılmıyor. .NET Framework Sınıf Kitaplığı'nda ek eski üyeler listesi için bkz: [eski üyeler](../../../docs/framework/whats-new/obsolete-members.md).  
  
-   [Sistem derlemelerde eski türler](#obsolete_types_in_system_assemblies)  
  
    -   [mscorlib.dll](#mscorlib)  
  
    -   [System.Core.dll](#Core)  
  
    -   [System.Data.dll](#data)  
  
    -   [System.Data.OracleClient.dll](#oracleclient)  
  
    -   [System.Design.dll](#design)  
  
    -   [System.dll](#system)  
  
    -   [System.EnterpriseServices.dll](#enterpriseservices)  
  
    -   [System.Net.dll](#net)  
  
    -   [System.ServiceModel.dll](#servicemodel)  
  
    -   [System.Web.dll](#web)  
  
    -   [System.Web.Mobile.dll](#mobile)  
  
    -   [System.Workflow.Activities.dll](#workflow_activities)  
  
    -   [System.Workflow.ComponentModel.dll](#workflow_componentmodel)  
  
    -   [System.Workflow.Runtime.dll](#workflow_runtime)  
  
    -   [System.WorkflowServices.dll](#workflowservices)  
  
    -   [System.Xaml.dll](#xaml)  
  
    -   [System.Xml.dll](#xml)  
  
    -   [WindowsBase.dll](#WindowsBase)  
  
-   [Microsoft derlemelerde eski türler](#obsolete_types_in_microsoft_assemblies)  
  
    -   [IEHost.dll ve IEExec.exe](#IEHost)  
  
    -   [Microsoft.Build.Engine.dll](#Engine)  
  
    -   [Microsoft.JScript.dll](#jscript)  
  
    -   [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)  
  
    -   [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)  
  
    -   [Microsoft.VisualC.dll](#visualc)  
  
<a name="obsolete_types_in_system_assemblies"></a>   
## <a name="obsolete-types-in-system-assemblies"></a>Sistem derlemelerde eski türler  
 Aşağıdaki tablolarda sistem derlemelerde artık kullanılmayan bildirilen türleri listelenmektedir. Bu derlemeler için genel kullanılan\-amaçla .NET Framework hedefleyen uygulama geliştirme.  
  
<a name="mscorlib"></a>   
### <a name="assembly-mscorlibdll"></a>Derleme: mscorlib.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|Bu tür daha önce bir belirtilmeyen hatayla çalışma zamanında gösterilir. Bu tür kullanılmıyor şekilde çalışma zamanı bu özel durum artık başlatır.|  
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|Lütfen kullanın <xref:System.StringComparer?displayProperty=nameWithType> yerine.|  
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|Lütfen kullanın <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType> yerine.|  
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash> Sınıfı kullanım dışı bırakıldı.|  
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı. Kullanım <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> System.Runtime.CompilerServices ad alanında yerine sınıfı.|  
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=nameWithType>|Alternatif bir API kullanılabilir: yayma <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> özel öznitelik yerine.|  
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
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|Bu öznitelik kullanım dışıdır ve gelecek sürümde kaldırılacak.|  
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> Kullanım dışı bırakılmıştır.|  
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType> kullanın.|  
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType> kullanın.|  
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType> kullanın.|  
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType> kullanın.|  
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType> kullanın.|  
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType> kullanın.|  
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|Bunun yerine <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType> kullanın.|  
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|Bu özniteliği kullanım dışı bırakıldı. Uygulama etki alanları artık etkinleştirme bağlamı sınırları IDispatch çağrılarında dikkate.|  
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
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope> yalnızca .NET 2.0 saydamlık uyumluluk için kullanılır.|  
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute> yalnızca .NET 2.0 saydamlık uyumluluk için kullanılır. Lütfen kullanın <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType> yerine.|  
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|Bu tür kullanımdan kalkmıştır ve .NET Framework'ün bir sonraki sürümde kaldırılacak.|  
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|Derleme düzeyi bildirim temelli güvenlik kullanımdan kalkmıştır ve artık CLR tarafından varsayılan olarak uygulanır.|  
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|Bu tür kullanımdan kalkmıştır ve .NET Framework'ün bir sonraki sürümde kaldırılacak.|  
  
 [Başa dön](#introduction)  
  
<a name="Core"></a>   
### <a name="assembly-systemcoredll"></a>Derleme: System.Core.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu tür kullanmayın.|  
  
 [Başa dön](#introduction)  
  
<a name="data"></a>   
### <a name="assembly-systemdatadll"></a>Derleme: System.Data.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute> kullanım dışıdır.|  
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes> kullanım dışıdır.|  
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|<xref:System.Data.TypedDataSetGenerator> Sınıfı bir sonraki sürümde kaldırılacak. Lütfen kullanın <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType> System.Design.dll içinde.|  
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|<xref:System.Xml.XmlDataDocument> Sınıfı bir sonraki sürümde kaldırılacak.|  
  
 [Başa dön](#introduction)  
  
<a name="oracleclient"></a>   
### <a name="assembly-systemdataoracleclientdll"></a>Derleme: System.Data.OracleClient.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleClientFactory> kullanım dışıdır.|  
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommand> kullanım dışıdır.|  
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommandBuilder> kullanım dışıdır.|  
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnection> kullanım dışıdır.|  
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder> kullanım dışıdır.|  
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleDataAdapter> kullanım dışıdır.|  
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermission> kullanım dışıdır.|  
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType> kullanım dışıdır.|  
  
 [Başa dön](#introduction)  
  
<a name="design"></a>   
### <a name="assembly-systemdesigndll"></a>Derleme: System.Design.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Bunun yerine <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType> kullanın.|  
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|Bu türün kullanımı aracılığıyla veri bağlamaları düzenleme başlatılır çünkü önerilmez bir <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> ve özellik ızgarasının yerine.|  
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|Bu türün kullanımı aracılığıyla veri bağlamaları düzenleme başlatılır çünkü önerilmez bir <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> ve özellik ızgarasının yerine.|  
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> ve <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> ve <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|Şablon düzenleme içinde işlendiğinden bu türün kullanımı önerilmez <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Şablon düzenleme desteklemek için şablon verileri kullanıma <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> özelliği ve çağrı <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsReferenceManager> Ek işlevler içerir ve daha fazla Genişletilebilirliğe izin verir. Alınacak <xref:System.Web.UI.Design.WebFormsReferenceManager>, kullanın `RootDesigner.ReferenceManager` özelliğinden, <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsRootDesigner> Ek işlevler içerir ve daha fazla Genişletilebilirliğe izin verir. Alınacak <xref:System.Web.UI.Design.WebFormsRootDesigner>, kullanın <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> özelliğinden, <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|Şablon düzenleme içinde işlendiğinden bu türün kullanımı önerilmez <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Şablon düzenleme desteklemek için şablon verileri kullanıma <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> özelliği ve çağrı <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType> kullandığından bir <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> içeriği düzenlemek için. Tasarımcı bölgeler için düzenlenmekte olan içeriğin daha iyi denetim sağlar.|  
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|Şablon düzenleme içinde işlendiğinden bu türün kullanımı önerilmez <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Şablon düzenleme desteklemek için şablon verileri kullanıma <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> özelliği ve çağrı <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|Şablon düzenleme içinde işlendiğinden bu türün kullanımı önerilmez <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Şablon düzenleme desteklemek için şablon verileri kullanıma <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> özelliği ve çağrı <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|Otomatik Biçim iletişim Tasarımcı ana bilgisayar tarafından başlatılan çünkü bu tür kullanılması önerilmez. Kullanılabilir otomatik biçimler listesi üzerinde gösterilen <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> içinde <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> özelliği.|  
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType> kullandığından bir <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> içeriği düzenlemek için. Tasarımcı bölgeler için düzenlenmekte olan içeriğin daha iyi denetim sağlar.|  
  
 [Başa dön](#introduction)  
  
<a name="system"></a>   
### <a name="assembly-systemdll"></a>Derleme: System.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|Bu arabirim kullanım dışı bırakıldı. Ekleme bir <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> türünü işlemek için <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType> yerine.|  
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|Kullanım <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> bunun yerine yeni ayarları modeli ile çalışmak üzere.|  
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|Bu özniteliği kullanım dışı bırakıldı. Bunun yerine <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType> kullanın. Örneğin, bir kök Tasarımcısı CodeDom için belirtmek için kullanın `DesignerSerializerAttribute\(...,typeof\(TypeCodeDomSerializer\)\)`.|  
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı.|  
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Performans sayaçları aracılığıyla kullanın <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> yerine sınıfı.|  
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Lütfen kullanın <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> yerine erişip genel varsayılan proxy ayarlayın. Kullanmak yerine 'null' <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>.|  
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
  
 [Başa dön](#introduction)  
  
<a name="enterpriseservices"></a>   
### <a name="assembly-systementerpriseservicesdll"></a>Derleme: System.EnterpriseServices.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|<xref:System.EnterpriseServices.RegistrationHelperTx> Sınıfı kullanım dışı bırakıldı.|  
  
 [Başa dön](#introduction)  
  
<a name="net"></a>   
### <a name="assembly-systemnetdll"></a>Derleme: System.Net.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
  
 [Başa dön](#introduction)  
  
<a name="servicemodel"></a>   
### <a name="assembly-systemservicemodeldll"></a>Derleme: System.ServiceModel.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Eş kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|  
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu tür kullanılmıyor. HTTP etkinleştirmek üzere <xref:System.Net.CookieContainer>, kullanın `AllowCookies` özelliğini Http bağlama veya üzerinde <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.|  
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Eş kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|  
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Eş kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Eş kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Eş kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|  
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Eş kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|  
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Eş kanal özelliği kullanımdan kalkmıştır ve gelecekte kaldırılacaktır.|  
  
 [Başa dön](#introduction)  
  
<a name="web"></a>   
### <a name="assembly-systemwebdll"></a>Derleme: System.Web.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|Bu tür kullanılmıyor. Passport kimlik doğrulama ürün artık desteklenmemektedir ve yerine geçen [Microsoft Account](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>.|  
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|Bu tür kullanılmıyor. Passport kimlik doğrulama ürün artık desteklenmemektedir ve yerine geçen [Microsoft Account](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|Bu tür kullanılmıyor. Passport kimlik doğrulama ürün artık desteklenmemektedir ve yerine geçen [Microsoft Account](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|Bu tür kullanılmıyor. Passport kimlik doğrulama ürün artık desteklenmemektedir ve yerine geçen [Microsoft Account](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|Bu tür kullanılmıyor. Passport kimlik doğrulama ürün artık desteklenmemektedir ve yerine geçen [Microsoft Account](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|Bu tür kullanılmıyor. Passport kimlik doğrulama ürün artık desteklenmemektedir ve yerine geçen [Microsoft Account](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|Önerilen alternatif <xref:System.Convert?displayProperty=nameWithType> ve <xref:System.String.Format%2A?displayProperty=nameWithType>.|  
  
 [Başa dön](#introduction)  
  
<a name="mobile"></a>   
### <a name="assembly-systemwebmobiledll"></a>Derleme: System.Web.Mobile.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll derleme kullanım dışı bırakıldı ve artık kullanılmalıdır. ASP.NET Mobil uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [kaydettiğinde için ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231).|  
  
 [Başa dön](#introduction)  
  
<a name="workflow_activities"></a>   
### <a name="assembly-systemworkflowactivitiesdll"></a>Derleme: System.Workflow.Activities.dll  
  
|Tür|İleti|  
|----------|-------------|  
|İçindeki tüm türler <xref:System.Workflow.Activities?displayProperty=nameWithType> ad alanı|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
  
 [Başa dön](#introduction)  
  
<a name="workflow_componentmodel"></a>   
### <a name="assembly-systemworkflowcomponentmodeldll"></a>Derleme: System.Workflow.ComponentModel.dll  
  
|Tür|İleti|  
|----------|-------------|  
|İçindeki tüm türler <xref:System.Workflow.ComponentModel> ad alanı dışında <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> ve <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|İçindeki tüm türler <xref:System.Workflow.ComponentModel.Compiler> ad alanı dışında <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> ve <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|İçindeki tüm türler <xref:System.Workflow.ComponentModel.Design> dışında ad alanı <xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
  
 [Başa dön](#introduction)  
  
<a name="workflow_runtime"></a>   
### <a name="assembly-systemworkflowruntimedll"></a>Derleme: System.Workflow.Runtime.dll  
  
|Tür|İleti|  
|----------|-------------| 
|<xref:System.Activities.Statements.Interop>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br />Workflow Foundation 3.0 türleri kullanım dışı bırakılmıştır. Bunun yerine, Workflow 4.0 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Activities.Tracking.InteropTrackingRecord>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br />Workflow Foundation 3.0 türleri kullanım dışı bırakılmıştır. Bunun yerine, Workflow 4.0 türlerinden kullanın <xref:System.Activities>.\*.|   
|İçindeki tüm türler <xref:System.Workflow.Runtime> ad alanı|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|İçindeki tüm türler <xref:System.Workflow.Runtime.Configuration> ad alanı|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|İçindeki tüm türler <xref:System.Workflow.Runtime.DebugEngine> dışında ad alanı <xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|İçindeki tüm türler <xref:System.Workflow.Runtime.Hosting> dışında ad alanı <xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
|İçindeki tüm türler <xref:System.Workflow.Runtime.Tracking> ad alanı|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> System.Workflow. \* türleri dışıdır. Bunun yerine, Lütfen yeni türlerinden kullanın <xref:System.Activities>.\*.|  
  
 [Başa dön](#introduction)  
  
<a name="workflowservices"></a>   
### <a name="assembly-systemworkflowservicesdll"></a>Derleme: System.WorkflowServices.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|İçindeki tüm türler <xref:System.Workflow.Activities?displayProperty=nameWithType> ad alanı|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine, Lütfen yeni WF 4 türlerinden kullanın <xref:System.Activities>.\*.|  
  
 [Başa dön](#introduction)  
  
<a name="xaml"></a>   
### <a name="assembly-systemxamldll"></a>Derleme: System.Xaml.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|Bu XAML ayrıştırıcı tarafından kullanılmaz. Lütfen bakmak <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>.|  
  
 [Başa dön](#introduction)  
  
<a name="xml"></a>   
### <a name="assembly-systemxmldll"></a>Derleme: System.Xml.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|Önce .NET Framework 4. 5 ' kullanım dışı.<br /><br /> Bu türün kullanımı derleyici hatası oluşturur.<br /><br /> Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|Kullanım <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> şema derleme ve doğrulama.|  
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|Kullanım bir <xref:System.Xml.XmlReader?displayProperty=nameWithType> tarafından oluşturulan <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> uygun kullanarak yöntemini <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType> yerine.|  
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|Bu türün kullanımı derleyici hatası oluşturur. Bu API, .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.|  
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Lütfen kullanın <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType> yerine.|  
  
 [Başa dön](#introduction)  
  
<a name="WindowsBase"></a>   
### <a name="assembly-windowsbasedll"></a>Derleme: WindowsBase.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType> kullanım dışıdır. Bu arabirim artık kullanımda.|  
  
 [Başa dön](#introduction)  
  
<a name="obsolete_types_in_microsoft_assemblies"></a>   
## <a name="obsolete-types-in-microsoft-assemblies"></a>Microsoft derlemelerde eski türler  
 Aşağıdaki bölümler Microsoft derlemelerde geçersiz türlerini listeler. Bu derlemeler (örneğin, Microsoft.JScript.dll veya Microsoft.VisualC.dll) tek bir dil hedef derlemeler gibi özel amaçlı derlemeleri ' dir.  
  
<a name="IEHost"></a>   
### <a name="assembly-iehostdll-and-ieexecexe"></a>Derleme: IEHost.dll ve IEExec.exe  
 IEHost.dll ve IEExec.exe derlemeler .NET Framework'teki kaldırılmıştır. Tüm bunların türleri ve üyeleri eskidir ve sürümünden desteklenmez [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Bu derlemeler Windows Forms denetimleri barındırmak için ve Internet Explorer'da yürütülebilir dosyaları çalıştırmak için kullanılmıştır. Önerilen alternatifleri ClickOnce, XAML tarayıcısı uygulamaları (XBAP) içerir ve Microsoft Silverlight.  
  
 [Başa dön](#introduction)  
  
<a name="Engine"></a>   
### <a name="assembly-microsoftbuildenginedll"></a>Derleme: Microsoft.Build.Engine.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Lütfen kullanın <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> gelen *Microsoft.Build* derleme yerine.|  
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|Bu sınıf kullanım dışı bırakıldı. Lütfen kullanın <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> gelen *Microsoft.Build* derleme yerine.|  
  
 [Başa dön](#introduction)  
  
<a name="jscript"></a>   
### <a name="assembly-microsoftjscriptdll"></a>Derleme: Microsoft.JScript.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|Visual Studio 2005'te onaylanmaz bu türün kullanımı önerilmez; Bu özellik için hiçbir değişiklik olacaktır. Lütfen bakın <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> Ek Yardım için belgeleri.|  
  
 [Başa dön](#introduction)  
  
<a name="VBCompat"></a>   
### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>Derleme: Microsoft.VisualBasic.Compatibility.dll  
  Visual Basic 6'dan geçiş hakkında daha fazla bilgi için bkz: [Visual Basic 6.0 Kaynak Merkezi](https://msdn.microsoft.com/library/windows/desktop/ms788229).
|Tür|İleti|  
|----------|-------------|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
  
 [Başa dön](#introduction)  
  
<a name="VBCompatData"></a>   
### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>Derleme: Microsoft.VisualBasic.Compatibility.Data.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=nameWithType>|Bu üye kullanılmıyor.|  
  
 [Başa dön](#introduction)  
  
<a name="visualc"></a>   
### <a name="assembly-microsoftvisualcdll"></a>Derleme: Microsoft.VisualC.dll  
  
|Tür|İleti|  
|----------|-------------|  
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll geçersiz bir derleme ve yalnızca geriye dönük uyumluluk yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sınıf Kitaplığında Artık Kullanılmayanlar](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Eski Üyeler](../../../docs/framework/whats-new/obsolete-members.md)
