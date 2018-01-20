---
title: "-appconfig (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3f2c1bc9d0d3fec0635d284f64138f0432f59ef
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="57cb0-102">-appconfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="57cb0-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="57cb0-103">**- Appconfig** derleyici seçeneği derleme bağlama zamanında ortak dil çalışma zamanı (CLR) için bir derlemenin uygulama yapılandırması (app.config) dosyasının konumunu belirtmek C# uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="57cb0-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57cb0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57cb0-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="57cb0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="57cb0-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="57cb0-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="57cb0-106">Required.</span></span> <span data-ttu-id="57cb0-107">Derleme bağlama ayarları içeren uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="57cb0-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57cb0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57cb0-108">Remarks</span></span>  
 <span data-ttu-id="57cb0-109">Bir kullanımını **- appconfig** Gelişmiş senaryoları bütünleştirilmiş olduğu .NET Framework sürümünü ve aynı anda belirli referans derlemesini Silverlight sürümü için .NET Framework başvurmak.</span><span class="sxs-lookup"><span data-stu-id="57cb0-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="57cb0-110">Örneğin, Windows Presentation Foundation (WPF) yazılmış bir XAML Tasarımcısı hem WPF Masaüstü için tasarımcının kullanıcı arabirimi ve Silverlight ile gelen WPF alt başvuru gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="57cb0-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="57cb0-111">Her iki derlemeleri erişmek aynı tasarımcı derlemesi vardır.</span><span class="sxs-lookup"><span data-stu-id="57cb0-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="57cb0-112">Derleme bağlama eşdeğer olarak iki derleme gördüğünden varsayılan olarak, bir derleyici hatası ayrı başvuruları neden.</span><span class="sxs-lookup"><span data-stu-id="57cb0-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="57cb0-113">**- Appconfig** derleyici seçeneği sağlar, kullanarak varsayılan davranışı devre dışı bırakan bir app.config dosyasının konumunu belirtmek bir `<supportPortability>` , aşağıdaki örnekte gösterildiği gibi etiketi.</span><span class="sxs-lookup"><span data-stu-id="57cb0-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="57cb0-114">Derleyici dosyasının konumunu CLR'nin derleme bağlama mantığı geçirir.</span><span class="sxs-lookup"><span data-stu-id="57cb0-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57cb0-115">Uygulamanızı yapılandırmak için Microsoft Build Engine (MSBuild) kullanıyorsanız, ayarlayabileceğiniz **- appconfig** .csproj dosyasına bir özellik etiketi ekleyerek derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="57cb0-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="57cb0-116">Projede zaten ayarlanmış app.config dosyasını kullanmak için özellik etiketi ekleyin `<UseAppConfigForCompiler>` .csproj için dosya ve değerini ayarlama `true`.</span><span class="sxs-lookup"><span data-stu-id="57cb0-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="57cb0-117">Farklı bir app.config dosyası belirtmek için özellik etiketi ekleyin `<AppConfigForCompiler>` ve dosya konumuna değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="57cb0-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57cb0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="57cb0-118">Example</span></span>  
 <span data-ttu-id="57cb0-119">Aşağıdaki örnek bir uygulama hem .NET Framework uygulamasını hem de her iki uygulamada da bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulama için .NET Framework başvuran sağlayan bir app.config dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="57cb0-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="57cb0-120">**- Appconfig** derleyici seçeneği bu app.config dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="57cb0-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57cb0-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57cb0-121">See Also</span></span>  
 [<span data-ttu-id="57cb0-122">\<supportPortability > öğesi</span><span class="sxs-lookup"><span data-stu-id="57cb0-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [<span data-ttu-id="57cb0-123">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="57cb0-123">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
