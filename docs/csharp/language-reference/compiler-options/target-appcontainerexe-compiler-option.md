---
title: '-target: appcontainerexe (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 4f8c59d94b76dd0f3415846f7e682d62cc1771ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707615"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="d76e3-102">-target: appcontainerexe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d76e3-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="d76e3-103">Kullanırsanız **-target: appcontainerexe** derleyici seçeneği, derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows yürütülebilir (.exe) dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d76e3-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="d76e3-104">Bu seçenek eşdeğerdir [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) için tasarlanmıştır ancak [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="d76e3-104">This option is equivalent to [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d76e3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d76e3-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="d76e3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d76e3-106">Remarks</span></span>  
 <span data-ttu-id="d76e3-107">Uygulamanın bir uygulama kapsayıcısında çalışmasını zorunlu kılmak için bu seçenek bir bit ayarlar [Taşınabilir Çalıştırılabilir](/windows/desktop/Debug/pe-format) (PE) dosyası.</span><span class="sxs-lookup"><span data-stu-id="d76e3-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="d76e3-108">Söz konusu bit ayarlandığında, CreateProcess yöntemi yürütülebilir dosyayı bir uygulama kapsayıcısı dışında çalıştırmayı denerse bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="d76e3-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="d76e3-109">Kullanmadığınız sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıkış dosyası adını içeren giriş dosyasının adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d76e3-109">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="d76e3-110">Tüm bir komut isteminde bu seçeneği belirttiğinizde, kadar sonraki dosyalar **-out** veya **-hedef** seçeneği, yürütülebilir dosyayı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d76e3-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="d76e3-111">Bu derleyici seçeneğini IDE içinde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d76e3-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="d76e3-112">İçinde **Çözüm Gezgini**, projeniz için kısayol menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d76e3-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="d76e3-113">Üzerinde **uygulama** sekmesinde **çıkış türü** listesinde **Windows Store App**.</span><span class="sxs-lookup"><span data-stu-id="d76e3-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="d76e3-114">Bu seçenek yalnızca kullanılabilir [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulama şablonları.</span><span class="sxs-lookup"><span data-stu-id="d76e3-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="d76e3-115">Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="d76e3-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d76e3-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d76e3-116">Example</span></span>  
 <span data-ttu-id="d76e3-117">Aşağıdaki komut `filename.cs` yalnızca bir uygulama kapsayıcısında çalıştırılabilen bir Windows yürütülebilir dosyasına.</span><span class="sxs-lookup"><span data-stu-id="d76e3-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d76e3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d76e3-118">See also</span></span>

- [<span data-ttu-id="d76e3-119">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d76e3-119">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="d76e3-120">-target: winexe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d76e3-120">-target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)
- [<span data-ttu-id="d76e3-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d76e3-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
