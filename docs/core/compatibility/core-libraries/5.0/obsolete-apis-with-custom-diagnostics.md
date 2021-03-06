---
title: 'Son değişiklik: varsayılan olmayan tanılama kimlikleriyle API kullanım dışı meler'
description: Bazı API 'Lerin özel bir tanılama KIMLIĞIYLE artık kullanılmıyor olarak işaretlendiğinden, çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 9aa4543ae6660f2d2fceac2419340bc6c90f1c54
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257381"
---
# <a name="api-obsoletions-with-non-default-diagnostic-ids"></a><span data-ttu-id="093fb-103">Varsayılan olmayan tanılama kimlikleri ile API kullanımdan kaldırılmaları</span><span class="sxs-lookup"><span data-stu-id="093fb-103">API obsoletions with non-default diagnostic IDs</span></span>

<span data-ttu-id="093fb-104">Bazı API 'Ler, .NET 5,0 ' den itibaren eski olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="093fb-104">Some APIs have been marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="093fb-105">Bu son değişiklik, *özel bir tanılama kimliğiyle* eski olarak işaretlenen API 'lere özeldir.</span><span class="sxs-lookup"><span data-stu-id="093fb-105">This breaking change is specific to APIs that have been marked as obsolete *with a custom diagnostic ID*.</span></span> <span data-ttu-id="093fb-106">C# derleyicisi için [CS0618](../../../../csharp/language-reference/compiler-messages/cs0618.md) olan varsayılan kullanımdan KALDıRMA tanılama kimliğini gizleme, bu API 'ler kullanıldığında derleyicinin ürettiği uyarıları göstermez.</span><span class="sxs-lookup"><span data-stu-id="093fb-106">Suppressing the default obsoletion diagnostic ID, which is [CS0618](../../../../csharp/language-reference/compiler-messages/cs0618.md) for the C# compiler, does not suppress the warnings that the compiler generates when these APIs are used.</span></span>

## <a name="change-description"></a><span data-ttu-id="093fb-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="093fb-107">Change description</span></span>

<span data-ttu-id="093fb-108">Önceki .NET sürümlerinde, bu API 'Ler herhangi bir derleme uyarısı olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="093fb-108">In previous .NET versions, these APIs can be used without any build warning.</span></span> <span data-ttu-id="093fb-109">.NET 5 ve sonraki sürümlerinde, bu API 'lerin kullanılması bir derleme zamanı uyarısı veya özel bir tanılama KIMLIĞIYLE hata üretir.</span><span class="sxs-lookup"><span data-stu-id="093fb-109">In .NET 5 and later versions, use of these APIS produces a compile-time warning or error with a custom diagnostic ID.</span></span> <span data-ttu-id="093fb-110">Özel tanılama kimliklerinin kullanımı, kullanım dışı bırakılmış uyarıları, kullanımdan kaldırma durumunda olmayan tüm uyarılar yerine tek tek bastırmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="093fb-110">The use of custom diagnostic IDs allows you to suppress the obsoletion warnings individually instead of blanket-suppressing all obsoletion warnings.</span></span>

<span data-ttu-id="093fb-111">Aşağıdaki tabloda, kullanımdan, kullanım dışı bırakılmış API 'Ler için özel tanılama kimlikleri ve bunlara karşılık gelen uyarı iletileri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="093fb-111">The following table lists the custom diagnostic IDs and their corresponding warning messages for obsoleted APIs.</span></span>

| <span data-ttu-id="093fb-112">Tanılama KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="093fb-112">Diagnostic ID</span></span> | <span data-ttu-id="093fb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="093fb-113">Description</span></span> | <span data-ttu-id="093fb-114">Önem derecesi</span><span class="sxs-lookup"><span data-stu-id="093fb-114">Severity</span></span> |
| - | - |
| `SYSLIB0001` | <span data-ttu-id="093fb-115">UTF-7 kodlaması güvenli değil ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="093fb-115">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="093fb-116">Bunun yerine UTF-8 kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="093fb-116">Consider using UTF-8 instead.</span></span> | <span data-ttu-id="093fb-117">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-117">Warning</span></span> |
| `SYSLIB0002` | <span data-ttu-id="093fb-118"><xref:System.Security.Permissions.PrincipalPermissionAttribute> çalışma zamanı tarafından kabul edilmez ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="093fb-118"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> | <span data-ttu-id="093fb-119">Hata</span><span class="sxs-lookup"><span data-stu-id="093fb-119">Error</span></span> |
| `SYSLIB0003` | <span data-ttu-id="093fb-120">Kod erişim güvenliği (CAS) çalışma zamanı tarafından desteklenmez veya kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="093fb-120">Code access security (CAS) is not supported or honored by the runtime.</span></span> | <span data-ttu-id="093fb-121">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-121">Warning</span></span> |
| `SYSLIB0004` | <span data-ttu-id="093fb-122">Kısıtlanmış yürütme bölgesi (CER) özelliği desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="093fb-122">The constrained execution region (CER) feature is not supported.</span></span> | <span data-ttu-id="093fb-123">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-123">Warning</span></span> |
| `SYSLIB0005` | <span data-ttu-id="093fb-124">Genel bütünleştirilmiş kod önbelleği (GAC) desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="093fb-124">The global assembly cache (GAC) is not supported.</span></span> | <span data-ttu-id="093fb-125">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-125">Warning</span></span> |
| `SYSLIB0006` | <span data-ttu-id="093fb-126"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> desteklenmez ve atar <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="093fb-126"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="093fb-127">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-127">Warning</span></span> |
| `SYSLIB0007` | <span data-ttu-id="093fb-128">Bu şifreleme algoritmasının varsayılan uygulanması desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="093fb-128">The default implementation of this cryptography algorithm is not supported.</span></span> | <span data-ttu-id="093fb-129">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-129">Warning</span></span> |
| `SYSLIB0008` | <span data-ttu-id="093fb-130"><xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator>API desteklenmez ve atar <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="093fb-130">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="093fb-131">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-131">Warning</span></span> |
| `SYSLIB0009` | <span data-ttu-id="093fb-132"><xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>Ve <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> yöntemleri desteklenmez ve throw <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="093fb-132">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="093fb-133">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-133">Warning</span></span> |
| `SYSLIB0010`| <span data-ttu-id="093fb-134">Bazı uzaktan iletişim API 'Leri desteklenmez ve throw <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="093fb-134">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="093fb-135">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-135">Warning</span></span> |
| `SYSLIB0011` | <span data-ttu-id="093fb-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serileştirme artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="093fb-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> | <span data-ttu-id="093fb-137">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-137">Warning</span></span> |
| `SYSLIB0012` | <span data-ttu-id="093fb-138"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> ve <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> yalnızca .NET Framework uyumluluk için dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="093fb-138"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="093fb-139">Bunun yerine <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="093fb-139">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> | <span data-ttu-id="093fb-140">Uyarı</span><span class="sxs-lookup"><span data-stu-id="093fb-140">Warning</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="093fb-141">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="093fb-141">Version introduced</span></span>

<span data-ttu-id="093fb-142">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="093fb-142">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="093fb-143">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="093fb-143">Recommended action</span></span>

- <span data-ttu-id="093fb-144">Uyarı üzerinde belirtilen URL bağlantısını kullanarak her bir tanılama KIMLIĞI için belirtilen yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="093fb-144">Follow the specific guidance provided for the each diagnostic ID using the URL link provided on the warning.</span></span>

- <span data-ttu-id="093fb-145">Bu Kullanımdan kaldırılmış olan uyarılar veya hatalar, eski türler veya Üyeler için standart tanılama KIMLIĞI kullanılarak bastırılamaz; `SYSLIBxxxx` bunun yerine özel tanılama kimliği değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="093fb-145">Warnings or errors for these obsoletions can't be suppressed using the standard diagnostic ID for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID value instead.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="093fb-146">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="093fb-146">Affected APIs</span></span>

### <a name="syslib0001"></a><span data-ttu-id="093fb-147">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="093fb-147">SYSLIB0001</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>
- <xref:System.Text.UTF7Encoding.%23ctor%2A>

### <a name="syslib0002"></a><span data-ttu-id="093fb-148">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="093fb-148">SYSLIB0002</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute.%23ctor(System.Security.Permissions.SecurityAction)>

### <a name="syslib0003"></a><span data-ttu-id="093fb-149">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="093fb-149">SYSLIB0003</span></span>

<span data-ttu-id="093fb-150">`System.Security.Permissions`Ad alanındaki sınıflar:</span><span class="sxs-lookup"><span data-stu-id="093fb-150">Classes in the `System.Security.Permissions` namespace:</span></span>

- <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryCollection?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryEnumerator?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionSetAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBase?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBaseEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNamePublicKeyBlob?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermissionAttribute?displayProperty=fullName>

<span data-ttu-id="093fb-151">Şuradan türetilen sınıflar `CodeAccessSecurityAttribute` :</span><span class="sxs-lookup"><span data-stu-id="093fb-151">Classes that derive from `CodeAccessSecurityAttribute`:</span></span>

- <xref:System.Configuration.ConfigurationPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.EventLogPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermissionAttribute?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermissionAttribute?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.DnsPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.SocketPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.WebPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermissionAttribute?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermissionAttribute?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermissionAttribute?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermissionAttribute?displayProperty=fullName>

<span data-ttu-id="093fb-152">Arabirimlerdeki</span><span class="sxs-lookup"><span data-stu-id="093fb-152">Interfaces:</span></span>

- <xref:System.Security.Permissions.IUnrestrictedPermission?displayProperty=fullName>
- <xref:System.Security.IPermission?displayProperty=fullName>
- <xref:System.Security.IStackWalk?displayProperty=fullName>
- <xref:System.Security.Policy.IIdentityPermissionFactory?displayProperty=fullName>

<span data-ttu-id="093fb-153">Uygulayan sınıflar `IStackWalk` :</span><span class="sxs-lookup"><span data-stu-id="093fb-153">Classes that implement `IStackWalk`:</span></span>

- <xref:System.Security.NamedPermissionSet?displayProperty=fullName>
- <xref:System.Security.PermissionSet?displayProperty=fullName>

<span data-ttu-id="093fb-154">Uygulayan sınıflar `IPermission` :</span><span class="sxs-lookup"><span data-stu-id="093fb-154">Classes that implement `IPermission`:</span></span>

- <xref:System.Security.CodeAccessPermission?displayProperty=fullName>

<span data-ttu-id="093fb-155">Şuradan türetilen sınıflar `CodeAccessPermission` :</span><span class="sxs-lookup"><span data-stu-id="093fb-155">Classes that derive from `CodeAccessPermission`:</span></span>

- <xref:System.Configuration.ConfigurationPermission?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermission?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermission?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermission?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermission?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermission?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermission?displayProperty=fullName>
- <xref:System.Net.DnsPermission?displayProperty=fullName>
- <xref:System.Net.SocketPermission?displayProperty=fullName>
- <xref:System.Net.WebPermission?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermission?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermission?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermission?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermission?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlLoadPermission?displayProperty=fullName>

<span data-ttu-id="093fb-156">Şuradan türetilen sınıflar `ResourcePermissionBase` :</span><span class="sxs-lookup"><span data-stu-id="093fb-156">Classes that derive from `ResourcePermissionBase`:</span></span>

- <xref:System.Diagnostics.EventLogPermission?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermission?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermission?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermission?displayProperty=fullName>

<span data-ttu-id="093fb-157">`System.Security.Permissions`Ad alanındaki numaralandırmalar:</span><span class="sxs-lookup"><span data-stu-id="093fb-157">Enums in the `System.Security.Permissions` namespace:</span></span>

- <xref:System.Security.Permissions.DataProtectionPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionResource?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageContainment?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAudio?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionImage?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionVideo?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionState?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionClipboard?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionWindow?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionLevel?displayProperty=fullName>

<span data-ttu-id="093fb-158">Kod erişimi güvenlik türlerine bağlı olan sınıflar ve Üyeler:</span><span class="sxs-lookup"><span data-stu-id="093fb-158">Classes and members that depend on code access security types:</span></span>

- <xref:System.AppDomain.PermissionSet?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.AllowReversePInvokeCallsAttribute?displayProperty=fullName>
- <xref:System.Security.HostProtectionException?displayProperty=fullName>
- <xref:System.Security.Policy.FileCodeGroup?displayProperty=fullName>
- <xref:System.Security.Policy.StrongName?displayProperty=fullName>
- <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=fullName>
- [<span data-ttu-id="093fb-159">System. Security. Policy. ApplicationTrust. ApplicationTrust (PermissionSet, IEnumerable \<StrongName> )</span><span class="sxs-lookup"><span data-stu-id="093fb-159">System.Security.Policy.ApplicationTrust.ApplicationTrust(PermissionSet, IEnumerable\<StrongName>)</span></span>](/dotnet/api/system.security.policy.applicationtrust.-ctor#System_Security_Policy_ApplicationTrust__ctor_System_Security_PermissionSet_System_Collections_Generic_IEnumerable_System_Security_Policy_StrongName__)
- <xref:System.Security.Policy.ApplicationTrust.FullTrustAssemblies?displayProperty=fullName>
- <xref:System.Security.Policy.GacInstalled?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyStatement.%23ctor%2A?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.AddNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.ChangeNamedPermissionSet(System.String,System.Security.PermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.GetNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=nameWithType>
- <xref:System.Security.Policy.PolicyStatement.PermissionSet?displayProperty=fullName>
- <xref:System.Security.Policy.Publisher?displayProperty=fullName>
- <xref:System.Security.Policy.Site?displayProperty=fullName>
- <xref:System.Security.Policy.Url?displayProperty=fullName>
- <xref:System.Security.Policy.Zone?displayProperty=fullName>
- <xref:System.Security.SecurityManager?displayProperty=fullName>

### <a name="syslib0004"></a><span data-ttu-id="093fb-160">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="093fb-160">SYSLIB0004</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

### <a name="syslib0005"></a><span data-ttu-id="093fb-161">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="093fb-161">SYSLIB0005</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

### <a name="syslib0006"></a><span data-ttu-id="093fb-162">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="093fb-162">SYSLIB0006</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

### <a name="syslib0007"></a><span data-ttu-id="093fb-163">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="093fb-163">SYSLIB0007</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

### <a name="syslib0008"></a><span data-ttu-id="093fb-164">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="093fb-164">SYSLIB0008</span></span>

- <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>

### <a name="syslib0009"></a><span data-ttu-id="093fb-165">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="093fb-165">SYSLIB0009</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

### <a name="syslib0010"></a><span data-ttu-id="093fb-166">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="093fb-166">SYSLIB0010</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

### <a name="syslib0011"></a><span data-ttu-id="093fb-167">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="093fb-167">SYSLIB0011</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

### <a name="syslib0012"></a><span data-ttu-id="093fb-168">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="093fb-168">SYSLIB0012</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>
