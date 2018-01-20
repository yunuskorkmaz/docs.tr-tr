---
title: "-target: appcontainerexe (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e49047ee5a639189331b89f3c5e16f6a1f1d4cd5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="26077-102">-target: appcontainerexe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="26077-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="26077-103">Kullanırsanız **-target: appcontainerexe** derleyici seçeneği derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows yürütülebilir dosyanın (.exe) dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26077-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="26077-104">Bu seçenek eşdeğerdir [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) için tasarlanmıştır ancak [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="26077-104">This option is equivalent to [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26077-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26077-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="26077-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26077-106">Remarks</span></span>  
 <span data-ttu-id="26077-107">Bir uygulama kapsayıcısında çalıştırmak için uygulamayı gerektirmek için bu seçeneği bir bit ayarlar [taşınabilir yürütülebilir](http://go.microsoft.com/fwlink/p/?LinkId=236960) (PE) dosyası.</span><span class="sxs-lookup"><span data-stu-id="26077-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) (PE) file.</span></span> <span data-ttu-id="26077-108">Bu bit ayarlandığında, bir uygulama kapsayıcısı dışında yürütülebilir dosyayı başlatma CreateProcess yöntemi çalışırsa, bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="26077-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="26077-109">Kullanmadığınız sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adını içeren giriş dosyası adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="26077-109">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="26077-110">Tüm bir komut isteminde bu seçeneği belirttiğinizde, sonraki kadar dosyaları **-out** veya **-hedef** seçeneği yürütülebilir dosyayı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26077-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="26077-111">Bu derleyici seçeneğini IDE içinde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="26077-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="26077-112">İçinde **Çözüm Gezgini**projeniz için kısayol menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="26077-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="26077-113">Üzerinde **uygulama** sekmesinde **çıktı türü** listesinde, seçin **Windows mağazası uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="26077-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="26077-114">Bu seçenek yalnızca için kullanılabilir [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulama şablonları.</span><span class="sxs-lookup"><span data-stu-id="26077-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="26077-115">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="26077-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26077-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="26077-116">Example</span></span>  
 <span data-ttu-id="26077-117">Aşağıdaki komut derlerken `filename.cs` yalnızca bir uygulama kapsayıcısında çalıştırılabilir bir Windows yürütülebilir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="26077-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="26077-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26077-118">See Also</span></span>  
 [<span data-ttu-id="26077-119">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="26077-119">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="26077-120">-target:winexe (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="26077-120">-target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [<span data-ttu-id="26077-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="26077-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
