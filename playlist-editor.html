// ============================================================
// Character Home Helper - 공통 유틸리티
// ============================================================

const HelperUtils = {
    // ==========================================
    // 데이터 파싱
    // ==========================================
    
    /**
     * export const xxx = ... 형식의 코드에서 데이터 추출
     */
    parseExportData(code, varName) {
        try {
            // export const varName = 제거
            const regex = new RegExp(`export\\s+const\\s+${varName}\\s*=\\s*`, 'g');
            let cleaned = code.replace(regex, '').trim();
            
            // 끝의 세미콜론 제거
            if (cleaned.endsWith(';')) {
                cleaned = cleaned.slice(0, -1);
            }
            
            // 안전하게 파싱
            const fn = new Function('return ' + cleaned);
            return fn();
        } catch (e) {
            throw new Error(`파싱 실패: ${e.message}`);
        }
    },

    /**
     * 데이터를 export const xxx = ... 형식으로 변환
     */
    generateExportCode(varName, data, options = {}) {
        const { pretty = true } = options;
        const json = pretty 
            ? JSON.stringify(data, null, 2)
            : JSON.stringify(data);
        return `export const ${varName} = ${json};`;
    },

    // ==========================================
    // 문자열 처리
    // ==========================================
    
    /**
     * 문자열 이스케이프 (JSON용)
     */
    escapeString(str) {
        if (!str) return '';
        return str
            .replace(/\\/g, '\\\\')
            .replace(/"/g, '\\"')
            .replace(/\n/g, '\\n')
            .replace(/\r/g, '\\r')
            .replace(/\t/g, '\\t');
    },

    /**
     * 백틱 이스케이프 (템플릿 리터럴용)
     */
    escapeBacktick(str) {
        if (!str) return '';
        return str.replace(/`/g, '\\`');
    },

    /**
     * HTML 이스케이프
     */
    escapeHtml(str) {
        if (!str) return '';
        const div = document.createElement('div');
        div.textContent = str;
        return div.innerHTML;
    },

    // ==========================================
    // 클립보드
    // ==========================================
    
    /**
     * 클립보드에 복사
     */
    async copyToClipboard(text) {
        try {
            await navigator.clipboard.writeText(text);
            return true;
        } catch {
            // 폴백: textarea 방식
            const textarea = document.createElement('textarea');
            textarea.value = text;
            document.body.appendChild(textarea);
            textarea.select();
            document.execCommand('copy');
            document.body.removeChild(textarea);
            return true;
        }
    },

    // ==========================================
    // UI 헬퍼
    // ==========================================
    
    /**
     * 토스트 메시지 표시
     */
    showToast(message, type = 'info', duration = 3000) {
        const existing = document.querySelector('.toast');
        if (existing) existing.remove();

        const toast = document.createElement('div');
        toast.className = 'toast';
        toast.style.background = {
            'info': '#1e293b',
            'success': '#16a34a',
            'error': '#dc2626',
            'warning': '#d97706'
        }[type] || '#1e293b';
        toast.textContent = message;
        document.body.appendChild(toast);

        setTimeout(() => {
            toast.style.opacity = '0';
            toast.style.transform = 'translateY(20px)';
            setTimeout(() => toast.remove(), 300);
        }, duration);
    },

    /**
     * 확인 다이얼로그
     */
    confirm(message) {
        return window.confirm(message);
    },

    // ==========================================
    // 폼 헬퍼
    // ==========================================
    
    /**
     * 폼 데이터 가져오기
     */
    getFormData(formEl) {
        const data = {};
        const inputs = formEl.querySelectorAll('input, textarea, select');
        inputs.forEach(input => {
            if (input.name) {
                if (input.type === 'checkbox') {
                    data[input.name] = input.checked;
                } else if (input.type === 'number') {
                    data[input.name] = input.value ? Number(input.value) : null;
                } else {
                    data[input.name] = input.value;
                }
            }
        });
        return data;
    },

    /**
     * 폼에 데이터 설정
     */
    setFormData(formEl, data) {
        Object.entries(data).forEach(([key, value]) => {
            const input = formEl.querySelector(`[name="${key}"]`);
            if (input) {
                if (input.type === 'checkbox') {
                    input.checked = Boolean(value);
                } else {
                    input.value = value ?? '';
                }
            }
        });
    },

    // ==========================================
    // 배열/객체 헬퍼
    // ==========================================
    
    /**
     * 배열 요소 이동
     */
    moveArrayItem(arr, fromIndex, toIndex) {
        const item = arr.splice(fromIndex, 1)[0];
        arr.splice(toIndex, 0, item);
        return arr;
    },

    /**
     * 깊은 복사
     */
    deepClone(obj) {
        return JSON.parse(JSON.stringify(obj));
    },

    /**
     * 다음 ID 생성 (배열용)
     */
    getNextId(arr, idField = 'id') {
        if (!arr || arr.length === 0) return 1;
        return Math.max(...arr.map(item => item[idField] || 0)) + 1;
    },

    // ==========================================
    // 특수 포맷터
    // ==========================================
    
    /**
     * 플레이리스트 코드 생성 (기존 형식 유지)
     */
    generatePlaylistCode(songs) {
        const items = songs.map(s => {
            const safeTitle = this.escapeString(s.title || '');
            const safeArtist = this.escapeString(s.artist || '');
            const safeLyrics = this.escapeBacktick(s.lyrics || '');
            const safeComment = this.escapeString(s.comment || '');
            const hashtagsJson = JSON.stringify(s.hashtags || []);
            
            return `    {
        id: ${s.id},
        title: "${safeTitle}",
        artist: "${safeArtist}",
        link: "${s.link || ''}",
        hashtags: ${hashtagsJson},
        comment: "${safeComment}",
        lyrics: \`${safeLyrics}\`
    }`;
        }).join(',\n');
        
        return `export const playlistData = [\n${items}\n];`;
    },

    /**
     * 캐릭터 코드 생성
     */
    generateCharacterCode(data) {
        // 복잡한 객체이므로 커스텀 포맷팅
        const code = JSON.stringify(data, null, 2);
        return `// ============================================================
// 캐릭터 데이터
// ============================================================

export const characterData = ${code};

// 하위 호환성을 위한 export
export const characterProfiles = characterData.profiles;`;
    },

    /**
     * 오너 코드 생성
     */
    generateOwnerCode(data) {
        const code = JSON.stringify(data, null, 4);
        return `export const ownerData = ${code};`;
    },

    /**
     * 모티프 코드 생성
     */
    generateMotifCode(data) {
        const code = JSON.stringify(data, null, 4);
        return `// 모티프 데이터 (공통)
export const motifData = ${code};`;
    },

    /**
     * 설정 코드 생성
     */
    generateConfigCode(data) {
        // config는 함수가 포함되어 있어 특별 처리 필요
        const staticParts = JSON.stringify({
            labels: data.labels,
            theme: data.theme,
            features: data.features,
            player: data.player,
            defaults: data.defaults,
            components: data.components,
            timing: data.timing,
            bgMusicSections: data.bgMusicSections,
            keepBgMusicSections: data.keepBgMusicSections
        }, null, 2);

        // api 부분은 함수가 있으므로 수동 생성
        return `// 앱 설정 (config)
export const config = ${staticParts.slice(0, -1)},
  api: {
    youtubeIframe: 'https://www.youtube.com/iframe_api',
    youtubeThumbnail: (videoId) => \`https://img.youtube.com/vi/\${videoId}/hqdefault.jpg\`,
    uiAvatars: (name, bg = '333', color = 'fff') =>
      \`https://ui-avatars.com/api/?name=\${encodeURIComponent(name)}&background=\${bg}&color=\${color}\`
  }
};`;
    },

    // ==========================================
    // 가사 포맷터
    // ==========================================
    
    formatLyrics(text, option, source) {
        let result = text;
        
        if (option === 3) { 
            // 3줄마다 빈 줄
            const lines = text.split('\n').map(l => l.trim()).filter(l => l !== '');
            let fmt = '';
            for (let i = 0; i < lines.length; i++) {
                fmt += lines[i] + '\n';
                if ((i + 1) % 3 === 0 && i !== lines.length - 1) fmt += '\n';
            }
            result = fmt.trim();
        } else if (option === 4) { 
            // 2줄 이상 빈 줄 → 1줄로
            result = text.split('\n').map(l => l.trim()).join('\n').replace(/\n{3,}/g, '\n\n').trim();
        } else if (option === 5) { 
            // 모든 빈 줄 제거
            result = text.split('\n').map(l => l.trim()).join('\n').replace(/\n{2,}/g, '\n').trim();
        }

        if (source) {
            result += result.length > 0 ? `\n\n( 출처 : ${source} )` : `( 출처 : ${source} )`;
        }
        
        return result;
    }
};

// 전역 노출
window.HelperUtils = HelperUtils;
