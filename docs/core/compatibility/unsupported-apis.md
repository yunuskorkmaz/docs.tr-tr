---
title: .NET Core 'da desteklenmeyen API 'Ler
titleSuffix: ''
description: .NET Core üzerinde her zaman bir özel durum oluşturan .NET Framework hangi API 'Leri öğrenin.
ms.date: 12/23/2019
ms.openlocfilehash: 94f334d7e4b7daf407f489ba274172ced9eefa81
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414441"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a>.NET Core üzerinde her zaman özel durum oluşturan API 'Ler

Aşağıdaki API 'Ler her zaman bir <xref:System.PlatformNotSupportedException> Platform alt kümesi üzerinde .NET Core üzerinde oluşturulur.

Bu makale, etkilenen API üyelerini ad alanına göre düzenler.

> [!NOTE]
>
> - Bu makale, devam eden bir çalışmadır. .NET Core üzerinde özel durum oluşturan API 'lerin tamamen bir listesi değildir.
> - Bu makale, .NET Core üzerinde throw ikili serileştirme için açık arabirim uygulamaları içermez. Daha fazla bilgi için bkz. [.NET Core 'Da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core).

## <a name="system"></a>Sistem

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | Tümü |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | Tümü |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | Tümü |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | Tümü |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Tümü |

## <a name="systemcodedomcompiler"></a>System. CodeDom. derleyicisi

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | Tümü |

## <a name="systemcollectionsspecialized"></a>System. Collections. özelleşmiş

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | Tümü |

## <a name="systemconfiguration"></a>System.Configurlama

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (tüm Üyeler) | Tümü |

## <a name="systemconsole"></a>System. Console

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType> (yalnızca Get) | Linux ve macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Console.Title?displayProperty=nameWithType> (yalnızca Get) | Linux ve macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |

## <a name="systemdatacommon"></a>System. Data. Common

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (atar <xref:System.NotSupportedException> ) | Tümü |

## <a name="systemdiagnosticsprocess"></a>System. Diagnostics. Process

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (yalnızca set) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (yalnızca set) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (yalnızca Get) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |

## <a name="systemio"></a>System.IO

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |

## <a name="systemiopipes"></a>System. ıO. Pipes

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (yalnızca set) | Linux ve macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux ve macOS |

## <a name="systemmedia"></a>System. Media

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |

## <a name="systemnet"></a>System.Net

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Tümü |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Tümü |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | Tümü |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |

## <a name="systemnetnetworkinformation"></a>System .net. NetworkInformation

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (UWP) |

## <a name="systemnetsockets"></a>System .net. Sockets

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | Tümü |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | Tümü |

## <a name="systemnetwebsockets"></a>System .net. WebSockets

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | Tümü |

## <a name="systemreflection"></a>System. Reflection

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | Tümü |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | Tümü |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | Tümü |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | Tümü |

## <a name="systemruntimecompilerservices"></a>System. Runtime. CompilerServices

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | Tümü |

## <a name="systemruntimeinteropservices"></a>System. Runtime. InteropServices

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | Tümü |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | Tümü |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | Tümü |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | Tümü |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux ve macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | Tümü |

## <a name="systemsecurity"></a>System. Security

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | Tümü |

## <a name="systemsecurityclaims"></a>System. Security. Claim

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | Tümü |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | Tümü |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |

## <a name="systemsecuritycryptography"></a>System. Security. Cryptography

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux ve macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Tümü |

## <a name="systemsecuritycryptographypkcs"></a>System. Security. Cryptography. Pkcs

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | Tümü |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | Tümü |

## <a name="systemsecuritycryptographyx509certificates"></a>System. Security. Cryptography. X509Certificates

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (yalnızca set) | Tümü |

## <a name="systemsecurityauthenticationextendedprotection"></a>System. Security. Authentication. ExtendedProtection

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |

## <a name="systemsecuritypolicy"></a>System. Security. Policy

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |

## <a name="systemserviceprocessservicecontroller"></a>System. ServiceProcess. ServiceController

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Tümü |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | Tümü |

## <a name="systemthreading"></a>System. Threading

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Tümü |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | Tümü |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | Tümü |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | Tümü |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | Tümü |

## <a name="systemxml"></a>System.Xml

| Üye | Oluşturan platformlar |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Tümü |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Tümü |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Tümü |

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 'den .NET Core 'a geçiş için son değişiklikler](fx-core.md)
- [.NET Core 'da ikili serileştirme](../../standard/serialization/binary-serialization.md#net-core)
- [.NET taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md)
